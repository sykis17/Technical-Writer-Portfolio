# Technical Enviroment Setup

To maintain a consistent documentation environment, the following commands are used to initialize the Docs-as-Code workspace.


## 1. Initializing the MkDocs Framework

### Prerequisites:

#### Python 3.x installed
#### Git installed and configured with a GitHub account
#### VS Code with the "Markdown All in One" extension (recommended)

### Install the MkDocs engine
`pip install mkdocs`

### Create the project structure
`mkdocs new .`

### Create file hierarchy
mkdocs.yml : The Configuration file

docs/index.md : Thee project landing page

docs/ : The directory containing all source Markdown files

## 2. Initializing Github

### Connect the local folder to the remote GitHub repository
`git remote add origin [https://github.com/YOUR_USERNAME/portfolio.git](https://github.com/YOUR_USERNAME/portfolio.git)`

### Set the primary branch to 'main'
`git branch -M main`

### Perform the initial upload
`git push -u origin main`


## 3. How to send changes to GitHub

### 1. Verification
#### Make your edits in the .md files.
#### CRITICAL: Update docs/revision-history.md with the new Revision Number and Date.
#### Run `mkdocs serve`on terminal to be able to check changes locally.

### 2. Stage Changes

#### `git status` To confirm modified files.
#### `git add .` Stage all changes for Upload.

### 3. Commit

#### `git commit -m "Brief description of the update"` (e.g., "Rev 1.3: Update Winter Ops Checklist)

### 4. Push to GitHub
#### `git push` Send your source code to the GitHub repository.

### 5. Deploy
#### `mkdocs gh-deploy` Updates the actual live website.

### 6. Final Cross-Check
#### `git status` Should report "Your branch is up to date" and "nothing to commit, working tree clean". 

## 4. Local Development (Live Preview)
`mkdocs serve`
The documentation will be available at http://127.0.0.1:8000

