# Documentation Workflow SOP

## Purpose
This document outlines the standard procedure for creating, versioning, and publishing Flight Operations documentation using the **Docs-as-Code** methodology.

## Tools & Environment
* **Authoring:** Visual Studio Code (Markdown)
* **Version Control:** Git & GitHub
* **Rendering Engine:** MkDocs (Material Theme)
* **Distribution:** Adobe Acrobat (PDF/A Optimized)


---

## 1. Authoring Process
All documents are authored in Markdown to ensure a clear separation between content and formatting. This allows for:
* Rapid updates during aircraft fleet changes.
* Consistency across different Emergency/Normal checklists.

## 2. Version Control (The Git Flow)
To ensure data integrity, every change follows a tracked workflow:
1. **Staging:** `git add .` (Preparing updates for the next release).
2. **Snapshot:** `git commit -m "Description of change"` (Creating a searchable history).
3. **Deployment:** `git push` (Syncing with the master repository).

## 3. Quality Assurance & Publishing
Before a document is released for EFB (Electronic Flight Bag) use:
* **Peer Review:** Changes are reviewed via GitHub Pull Requests.
* **Acrobat Optimization:** The final HTML/Markdown output is converted to PDF.
* **Technical Check:** Hyperlinks (like the one in the Cabin Altitude QRH) are verified for iPad compatibility.

---
*End of Procedure*
