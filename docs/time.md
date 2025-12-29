# Operations & Time Management

This tool provides synchronized time tracking for global operations. Use the Chronometer to track specific flight phases or training intervals.

---

<div id="clock-container" style="background: #1a1a1a; color: #00ff00; padding: 25px; border-radius: 12px; font-family: 'Courier New', Courier, monospace; border: 2px solid #333;">
    
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; text-align: center;">
        <div style="border: 1px solid #333; padding: 15px; border-radius: 8px;">
            <p style="margin: 0; color: #888; font-size: 0.8em;">UTC / ZULU</p>
            <h2 id="utc-time" style="margin: 10px 0; font-size: 1.8em; color: #00ff00 !important;">00:00:00</h2>
            <span style="font-size: 0.7em; color: #008800;">● SYSTEM ADVSY</span>
        </div>
        <div style="border: 1px solid #333; padding: 15px; border-radius: 8px;">
            <p style="margin: 0; color: #888; font-size: 0.8em;">HELSINKI (EET)</p>
            <h2 id="hel-time" style="margin: 10px 0; font-size: 1.8em; color: #00ff00 !important;">00:00:00</h2>
            <span style="font-size: 0.7em; color: #008800;">● LOCAL TIME</span>
        </div>
        <div style="border: 1px solid #333; padding: 15px; border-radius: 8px;">
            <p style="margin: 0; color: #888; font-size: 0.8em;">NEW YORK (EST)</p>
            <h2 id="ny-time" style="margin: 10px 0; font-size: 1.8em; color: #00ff00 !important;">00:00:00</h2>
            <span style="font-size: 0.7em; color: #008800;">● OPS CTR</span>
        </div>
        <div style="border: 1px solid #333; padding: 15px; border-radius: 8px;">
            <p style="margin: 0; color: #888; font-size: 0.8em;">HAWAII (HST)</p>
            <h2 id="hwi-time" style="margin: 10px 0; font-size: 1.8em; color: #00ff00 !important;">00:00:00</h2>
            <span style="font-size: 0.7em; color: #008800;">● PACIFIC HUB</span>
        </div>
    </div>

<div style="margin-top: 30px; text-align: center; border-top: 1px solid #333; padding-top: 20px;">
        <p style="margin: 0; color: #888; font-size: 0.8em;">FLIGHT CHRONOMETER</p>
        <h1 id="stopwatch-display" style="font-size: 3.5em; margin: 10px 0; color: #00ff00 !important;">00:00:00</h1>
        
<div style="display: flex; justify-content: center; gap: 10px; margin-bottom: 20px;">
            <button onclick="startStopwatch()" style="background: #3f51b5; color: white; border: none; padding: 12px 25px; border-radius: 4px; cursor: pointer; font-weight: bold;">START / STOP</button>
            <button onclick="recordLap()" style="background: #008800; color: white; border: none; padding: 12px 25px; border-radius: 4px; cursor: pointer; font-weight: bold;">ELAPSED MARK</button>
            <button onclick="resetStopwatch()" style="background: #444; color: white; border: none; padding: 12px 25px; border-radius: 4px; cursor: pointer; font-weight: bold;">RESET</button>
        </div>

<div id="laps-container" style="max-height: 150px; overflow-y: auto; background: #111; padding: 10px; border-radius: 5px; text-align: left; font-size: 0.9em; border: 1px solid #222;">
            <p style="color: #666; margin: 0; border-bottom: 1px solid #222; padding-bottom: 5px;">ELAPSED LOG:</p>
            <ul id="laps-list" style="list-style: none; padding: 0; margin: 5px 0; color: #00aa00;">
                </ul>
        </div>
    </div>

</div>

<script>
    function updateClocks() {
        const now = new Date();
        const options = { hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false };
        
        document.getElementById('utc-time').innerText = now.toLocaleTimeString('en-GB', { ...options, timeZone: 'UTC' });
        document.getElementById('hel-time').innerText = now.toLocaleTimeString('en-GB', { ...options, timeZone: 'Europe/Helsinki' });
        document.getElementById('ny-time').innerText = now.toLocaleTimeString('en-GB', { ...options, timeZone: 'America/New_York' });
        document.getElementById('hwi-time').innerText = now.toLocaleTimeString('en-GB', { ...options, timeZone: 'Pacific/Honolulu' });
    }
    setInterval(updateClocks, 1000);
    updateClocks();

    let startTime, elapsedTime = 0, timerInterval;
    let lapCount = 0;

    function startStopwatch() {
        if (!timerInterval) {
            startTime = Date.now() - elapsedTime;
            timerInterval = setInterval(() => {
                elapsedTime = Date.now() - startTime;
                document.getElementById('stopwatch-display').innerText = formatTime(elapsedTime);
            }, 100);
        } else {
            clearInterval(timerInterval);
            timerInterval = null;
        }
    }

    function recordLap() {
        if (elapsedTime > 0) {
            lapCount++;
            const list = document.getElementById('laps-list');
            const entry = document.createElement('li');
            entry.style.borderBottom = "1px solid #222";
            entry.style.padding = "3px 0";
            entry.innerHTML = `<span>MARK ${lapCount}:</span> <span style="float:right;">${formatTime(elapsedTime)}</span>`;
            list.prepend(entry);
        }
    }

    function resetStopwatch() {
        clearInterval(timerInterval);
        timerInterval = null;
        elapsedTime = 0;
        lapCount = 0;
        document.getElementById('stopwatch-display').innerText = "00:00:00";
        document.getElementById('laps-list').innerHTML = "";
    }

    function formatTime(ms) {
        let h = Math.floor(ms / 3600000);
        let m = Math.floor((ms % 3600000) / 60000);
        let s = Math.floor((ms % 60000) / 1000);
        return [h, m, s].map(v => v < 10 ? "0" + v : v).join(":");
    }
</script>