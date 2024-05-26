
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

## Adding an Azure SQL Database to the Environment

Follow these steps to integrate an Azure SQL Database into your project:

### Step 1: Set Up Your Azure Database

1. **Create an Azure SQL Database**:
   - Log in to the [Azure Portal](https://portal.azure.com/).
   - Click on `Create a resource` and select `SQL Database`.
   - Fill in the required details to create a new SQL database and server.

2. **Obtain Connection Details**:
   - Once the database is created, navigate to the database and find the connection string in the `Connection strings` section.
   - Note down the server name, database name, username, and password.

### Step 2: Install Required Packages

Activate your virtual environment and run the following commands:

```sh
pip install pyodbc
pip install azure-identity
pip install python-dotenv
```

### Step 3: Configure the Database Connection in Your Environment

1. **Create a Configuration File**:
   - Create a file named `config.py` in your project directory to store the connection configuration.

   ```python
   import os
   from dotenv import load_dotenv

   load_dotenv()

   DATABASE_CONFIG = {
       'server': os.getenv('DB_SERVER', 'your_server.database.windows.net'),
       'database': os.getenv('DB_NAME', 'your_database'),
       'username': os.getenv('DB_USERNAME', 'your_username'),
       'password': os.getenv('DB_PASSWORD', 'your_password')
   }
   ```

2. **Set Environment Variables**:
   - It’s a good practice to store sensitive information like database credentials in environment variables. You can set these in your operating system or use a `.env` file.

   Create a `.env` file in your project directory:

   ```plaintext
   DB_SERVER=your_server.database.windows.net
   DB_NAME=your_database
   DB_USERNAME=your_username
   DB_PASSWORD=your_password
   ```

### Step 4: Connect to the Azure Database

Create a Python script or Jupyter notebook to connect to the Azure database using the `pyodbc` package.

Here’s an example script (`connect_db.py`):

```python
import pyodbc
from config import DATABASE_CONFIG

# Construct the connection string
connection_string = (
    f"DRIVER={{ODBC Driver 17 for SQL Server}};"
    f"SERVER={DATABASE_CONFIG['server']};"
    f"DATABASE={DATABASE_CONFIG['database']};"
    f"UID={DATABASE_CONFIG['username']};"
    f"PWD={DATABASE_CONFIG['password']}"
)

# Establish the connection
try:
    conn = pyodbc.connect(connection_string)
    print("Connection successful!")
except Exception as e:
    print(f"Error: {e}")

# Sample query
cursor = conn.cursor()
cursor.execute("SELECT @@VERSION")
row = cursor.fetchone()
while row:
    print(row[0])
    row = cursor.fetchone()

# Close the connection
conn.close()
```

### Step 5: Run the Script

Run the script to test the connection:

```sh
python connect_db.py
```

### Step 6: Use the Database in Your Jupyter Notebook

You can also connect to the Azure database in a Jupyter Notebook. Here’s an example:

```python
import pyodbc
from config import DATABASE_CONFIG

# Construct the connection string
connection_string = (
    f"DRIVER={{ODBC Driver 17 for SQL Server}};"
    f"SERVER={DATABASE_CONFIG['server']};"
    f"DATABASE={DATABASE_CONFIG['database']};"
    f"UID={DATABASE_CONFIG['username']};"
    f"PWD={DATABASE_CONFIG['password']}"
)

# Establish the connection
conn = pyodbc.connect(connection_string)
print("Connection successful!")

# Sample query
cursor = conn.cursor()
cursor.execute("SELECT @@VERSION")
row = cursor.fetchone()
while row:
    print(row[0])
    row = cursor.fetchone()

# Close the connection
conn.close()
```

By following these steps, you will be able to integrate an Azure SQL Database into your environment and use it in your project.
