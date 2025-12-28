# Electrical System Logic

``` mermaid
graph TB
    subgraph AC_SOURCES [AC Power Sources]
        GEN1[Engine Gen 1]
        GEN2[Engine Gen 2]
        APU[APU Generator]
        EXT[External Power]
    end

    subgraph BUS_DISTRIBUTION [Bus Distribution]
        B1[AC Transfer Bus 1]
        B2[AC Transfer Bus 2]
    end

    GEN1 --> B1
    GEN2 --> B2
    
    APU -.->|Manual| B1
    APU -.->|Manual| B2
    
    EXT -.->|Avail| B1
    
    B1 --- TIE{Bus Tie} --- B2

    subgraph DC_SYSTEM [DC Power]
        TR1[TR 1]
        TR2[TR 2]
        BATT[Main Battery]
    end

    B1 --> TR1 --> DC1[DC Bus 1]
    B2 --> TR2 --> DC2[DC Bus 2]
    DC1 --> STBY[Standby Bus]
    BATT -.->|Emergency| STBY

    

    style STBY fill:#f96,stroke:#333,stroke-width:2px
    style TIE fill:#fff,stroke:#333,stroke-dasharray: 5 5

```