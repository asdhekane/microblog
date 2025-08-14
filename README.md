Below is the complete README file for the asdhekane/microblog repository in English. It is organized into the required sections and includes detailed information drawn directly from the repository source code.

------------------------------------------------------------

# Microblog

A simple microblogging web application built on Flask. This project demonstrates real-world usage of Flask features including user authentication, posting updates, following accounts, internationalization, error logging, and email integration. The application also uses SQLAlchemy as its ORM and supports database migrations via Flask-Migrate. The code is organized with blueprints for modularity and utilizes JWT for secure password reset tokens. fileciteturn0file7

------------------------------------------------------------

## Introduction

Microblog is a lightweight, yet functional, blog application designed as a learning resource and proof-of-concept web application. It illustrates how to use core Flask extensions such as Flask-Login for user authentication, Flask-Mail for email alerts, Flask-Migrate for database updates, and Flask-Babel for localization. The application showcases robust modular design by splitting routes into separate blueprints (for example, the auth and main blueprints) and by enforcing best practices for configuration management with environment variables. fileciteturn0file5

------------------------------------------------------------

## Features

- **User Authentication:** Secure user login, registration, and password reset functionality using JWT tokens.
- **Posting and Timeline:** Create, edit, and display short posts. The main timeline displays posts ordered by timestamp.
- **Profile Management:** Users can follow or unfollow other users and view profiles with latest activity. fileciteturn0file13
- **Internationalization:** Built-in i18n and l10n support with Flask-Babel facilitating multiple languages (English and Spanish).
- **Email Integration:** Sends password reset emails using Flask-Mail. fileciteturn0file1
- **Database Migrations:** SQLAlchemy together with Flask-Migrate handles database schema evolution.
- **Logging:** Error handling and logging support via SMTPHandler and RotatingFileHandler, ensuring errors are emailed and logged to disk.

------------------------------------------------------------

## Requirements

To run Microblog, ensure your development environment meets these requirements:

| **Software/Package**      | **Version/Notes**                                |
|---------------------------|--------------------------------------------------|
| **Python**                | 3.7 or higher                                    |
| **Flask**                 | Latest version (Flask 2.x recommended)           |
| **Flask-SQLAlchemy**      | For ORM/database interactions                    |
| **Flask-Migrate**         | For managing database migrations                 |
| **Flask-Login**           | For user session management                      |
| **Flask-Mail**            | To send emails (e.g., password resets)           |
| **Flask-Moment**          | For date/time display formatting                 |
| **Flask-Babel**           | For internationalization and localization         |
| **python-dotenv**         | For environment variable management              |
| **JWT (PyJWT)**           | For secure tokens used in password reset flows   |

Additional libraries such as WTForms and SQLAlchemy are also utilized. See the source configuration in config.py for further details on environment-specific settings. fileciteturn0file7

------------------------------------------------------------

## Installation

1. **Clone the repository:**

   Run the following command in your terminal:
   
   ```
   git clone https://github.com/asdhekane/microblog.git
   cd microblog
   ```

2. **Create a virtual environment and activate it:**

   On macOS and Linux:
   
   ```
   python3 -m venv venv
   source venv/bin/activate
   ```
   
   On Windows:
   
   ```
   python -m venv venv
   venv\Scripts\activate
   ```

3. **Install dependencies:**

   Use pip to install the required packages. If a requirements.txt file is provided, run:
   
   ```
   pip install -r requirements.txt
   ```
   
   Otherwise, install the necessary packages individually:
   
   ```
   pip install Flask Flask-SQLAlchemy Flask-Migrate Flask-Login Flask-Mail Flask-Moment Flask-Babel python-dotenv PyJWT
   ```

4. **Set up environment variables:**

   Create a `.env` file in the project root (alternatively, use the provided `.flaskenv` file) with at least the following content:
   
   ```
   SECRET_KEY=your-secret-key
   DATABASE_URL=sqlite:///app.db
   MAIL_SERVER=localhost
   MAIL_PORT=8025
   LANGUAGES=en,es
   ```
   
   This example matches the template found in the repository’s .flaskenv file. fileciteturn0file7

5. **Initialize the database:**

   Run the following commands to set up the database structure:
   
   ```
   flask db init
   flask db migrate -m "Initial migration."
   flask db upgrade
   ```

------------------------------------------------------------

## Usage

1. **Running the Application:**

   Launch the Microblog application using Flask’s development server:
   
   ```
   flask run
   ```
   
   Alternatively, you can run the microblog.py script directly:
   
   ```
   python microblog.py
   ```
   
   This starts the server on the default port (5000) so you can access it locally in your web browser.

2. **Accessing the Shell:**

   The application provides a shell context via a shell context processor so that you have direct access to the database and models:
   
   ```
   flask shell
   ```
   
   This opens an interactive Python shell with pre-imported objects (such as db, User, Post). fileciteturn0file10

3. **Interacting with the Application:**

   - **User Authentication:** Register as a new user or sign in using the login form.
   - **Posting:** Create new micro-posts which appear on the timeline.
   - **Following:** Visit other user profiles to follow or unfollow them.
   - **Password Reset:** Use the “Reset Your Password” feature that sends an email to the registered address.
   - **Language Preferences:** Switch between supported languages (English and Spanish) as Flask-Babel handles locale selection based on browser preferences.

------------------------------------------------------------

## Configuration

The Microblog application is highly configurable via environment variables and the configuration class in `config.py`. The key configuration details include:

- **SECRET_KEY:**  
  Used for securely signing session cookies and tokens. Set this to a strong, unique value.
  
- **SQLALCHEMY_DATABASE_URI:**  
  Database connection string. By default, the app uses a SQLite database (`app.db`). You can update this to point to a PostgreSQL or MySQL database if needed.
  
- **MAIL_SERVER, MAIL_PORT, MAIL_USERNAME, MAIL_PASSWORD, MAIL_USE_TLS:**  
  Settings for sending emails. These control how the application sends security and password reset emails.
  
- **ADMINS:**  
  A list of administrator email addresses. Error notifications and other critical alerts are sent to these addresses.
  
- **LANGUAGES:**  
  A list of supported languages. The application supports English and Spanish to demonstrate internationalization through Flask-Babel.
  
- **POSTS_PER_PAGE:**  
  Defines how many posts are displayed per page in the timeline.
  
All these settings can be adjusted in either the `.env` file (which is automatically loaded using python-dotenv) or directly via environment variables on your deployment platform. The application's configuration routine in `config.py` (which loads environment variables) ensures that these values are available throughout the application. fileciteturn0file7

------------------------------------------------------------

This README provides detailed documentation on the purpose, features, installation, usage, and configuration of the Microblog application. Feel free to contribute, raise issues, or expand on any sections as the project evolves. Enjoy building and learning with Microblog!
