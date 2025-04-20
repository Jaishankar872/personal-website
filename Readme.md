## Perquisites
1. Python3 and pip package
2. mkdocs-material
```bash
pip install mkdocs-material
```
3. VScode with Extensions (yaml)
4. Git

## Procedure to setup environment  
> **Note**: Below command work well with windows 
1. Clone this github repository
```bash
git clone https://github.com/Jaishankar872/personal-website.git
```
2. Create & Activate the Virtual Env in python
```bash
python -m venv venv
.\venv\Scripts\activate
```
3. Check the Pip & install the mkdocs [**Inside Virtual Env**]
``` 
pip --version
pip install mkdocs-material
```
4. Initial setup $\rightarrow$ open VScode & start server
```
cd personal-website
code .
mkdocs serve
```