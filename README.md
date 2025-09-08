# SQL Injection Demonstration with Flask and SQLite
` original project-code-base language: Spanish 🇪🇸`

This project is a basic web application in Flask designed to demonstrate the dangers of SQL injections. **It should not be used in production or with real data**. The application allows a user to log in using credentials stored in an SQLite database. However, the way the SQL query is built in this application makes it vulnerable to SQL injection attacks.

## Warning

**This project is intentionally insecure and should only be used for educational purposes.** Do not deploy it in any real environment. The goal is to show how poorly implemented SQL queries can be manipulated to execute unwanted commands.

## Requirements

- Python 3.7 or higher
- Flask 2.3.2

## Installation

1. Clone the repository or download the files.

2. Navigate to the project directory.

3. Install the dependencies using `pip`:

   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Initialize the database:

   The database is automatically initialized when the application is run for the first time. The `init_db()` function creates a `usuarios` table if it doesn’t exist.

2. Run the application:

   ```bash
   python app.py
   ```

3. Open your browser and go to `http://127.0.0.1:5000/` to access the application.

4. Try logging in using the credentials stored in the database, or test with a basic SQL injection such as:

   ```plaintext
   user: ' OR '1'='1
   password: ' OR '1'='1
   ```

   This should allow you to log in without knowing the correct username or password, thereby demonstrating the vulnerability.

## Project Structure

- `app.py`: The main file containing the Flask application logic.
- `templates/`: Directory containing the HTML files for the views.
  - `login.html`: Login page.
  - `success.html`: Page displayed upon successful login.
- `usuarios.db`: SQLite database that stores the usernames and passwords.

## Notes

- The application is configured to run in debug mode (`debug=True`), which is useful for development. Do not forget to disable this mode in a production environment.
- **The code intentionally builds insecure SQL queries for educational purposes.** This pattern should not be followed in real applications.
- To protect against SQL injections, SQL queries should be parameterized, meaning you should not directly concatenate user input into queries.
