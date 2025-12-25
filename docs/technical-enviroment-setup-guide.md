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

### 1. To check for status
`git status`

### 2. Add files
`git add .`

### 3. Commit the changes
`git commit -m "Added Cabin Altitude QRH and basic structure"`

### 5. Push to GitHub
Upload your local changes to the cloud:
`git push`

### 6. To check for status
`git status`

## 4. Local Development (Live Preview)
`mkdocs serve`
The documentation will be available at http://127.0.0.1:8000

