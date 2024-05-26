
# Jupyter Notebook Project Setup

This repository contains a Jupyter Notebook project. Follow the instructions below to set up the project on your local machine.

## Prerequisites

- [Python](https://www.python.org/downloads/) (Make sure to check "Add Python to PATH" during installation)
- [Git](https://git-scm.com/)
- [Visual Studio Code (VS Code)](https://code.visualstudio.com/)

## Installation Instructions

### Step 1: Clone the Repository

First, clone the repository to your local machine:

```sh
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

### Step 2: Create and Activate a Virtual Environment

Create a virtual environment to manage dependencies:

```sh
python -m venv venv
```

Activate the virtual environment:

- On Windows:
  ```sh
  .\venv\Scripts\activate
  ```
- On macOS/Linux:
  ```sh
  source venv/bin/activate
  ```

### Step 3: Install Jupyter Notebook

With the virtual environment activated, install Jupyter Notebook:

```sh
pip install jupyter
```

### Step 4: Set Up Jupyter Notebook in VS Code

1. **Open VS Code**.
2. **Install the Python Extension**:
   - Press `Ctrl + Shift + X` or click the Extensions icon in the Activity Bar.
   - Search for "Python" and install the extension by Microsoft.

3. **Select the Python Interpreter**:
   - Press `Ctrl + Shift + P` to open the Command Palette.
   - Type `Python: Select Interpreter` and select the virtual environment's interpreter.

4. **Create a New Jupyter Notebook**:
   - Press `Ctrl + Shift + P` again and type `Jupyter: Create New Blank Notebook`.
   - Save the new notebook file with a `.ipynb` extension.

### Step 5: Write and Run a "Hello World" Example

In the new notebook, create a cell with the following code:

```python
print("Hello, World!")
```

Run the cell by clicking the `Run` button or pressing `Shift + Enter`.

### Step 6: Deactivate the Virtual Environment (When Done)

To deactivate the virtual environment, run:

```sh
deactivate
```

## Additional Information

### .gitignore

This repository includes a `.gitignore` file configured to exclude the `venv` directory and other unnecessary files:

```plaintext
venv/
.ipynb_checkpoints/
.vscode/
__pycache__/
*.py[cod]
```

### Pushing Changes to GitHub

After making changes, you can add, commit, and push your changes to GitHub:

```sh
git add .
git commit -m "Your commit message"
git push origin main
```

Replace `main` with the appropriate branch name if you are using a different branch.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Happy coding!
