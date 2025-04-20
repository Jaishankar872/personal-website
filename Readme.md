## Prerequisites

Ensure the following tools and packages are installed:

1. **Python 3** and **pip** package manager.  
2. **MkDocs Material**, Install it using:  
   ```bash
   pip install mkdocs-material
   ```
3. **Visual Studio Code (VSCode)** with the **YAML** extension.  
4. **Git**.

## Procedure to Set Up the Environment  

> **Note:** The following commands are tailored for Windows systems.

1. Clone this GitHub repository to your local machine and Navigate to the project directory:  
    ```bash
    git clone https://github.com/Jaishankar872/personal-website.git
    cd personal-website
    code .
    ```
2. Set up a Python virtual environment and activate it:  
    ```bash
    python -m venv venv
    .\venv\Scripts\activate
    ```
3. Verify `pip` is working and install MkDocs Material **inside the virtual environment**:  
    ```bash
    pip --version
    pip install mkdocs-material
    ```
4. In VSCode, and start the MkDocs server:  
    ```bash
    mkdocs serve
    ```