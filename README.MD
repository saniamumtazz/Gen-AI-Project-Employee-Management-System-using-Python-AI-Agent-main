# AI Employee Database Agent

This project is a Python-based AI assistant that lets users manage an employee database using natural-language requests. Instead of writing SQL manually, the user asks the agent to create, read, update, delete, or search employee records, and the AI uses OpenAI function calling to perform the correct database action.

## Features

- Natural-language employee management via AI
- SQLite database backend
- Create, read, update, and delete employee records
- Search employees by name, department, city, and salary range
- Get employee counts and highest salary information
- Streamlit web interface for easy interaction
- Optional command-line agent mode

## Tech Stack

- Python
- OpenAI API
- SQLite
- Streamlit
- python-dotenv

## Project Structure

- `agent.py` — defines the OpenAI tool-calling workflow and the `ask_agent()` function.
- `app.py` — Streamlit UI for interacting with the AI employee database agent.
- `database.py` — SQLite database logic and employee-related CRUD/search functions.
- `test_agent.py` — sample script to test the AI agent in terminal mode.
- `test_database.py` — sample script to test database operations.
- `employees.db` — SQLite database file created automatically when the app runs.
- `requirements.txt` — project dependencies.

## How It Works

1. The user enters a request in natural language.
2. The AI model receives the request and decides which function to call.
3. The chosen Python function interacts with the SQLite database.
4. The result is sent back to the AI model.
5. The AI responds in a human-friendly way.

This means the user never needs to write raw SQL queries directly.

## Installation

1. Open a terminal in the project folder.
2. Create a virtual environment:

```bash
python -m venv venv
```

3. Activate the virtual environment:

Windows:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

4. Install the dependencies:

```bash
pip install -r requirements.txt
```

## Environment Setup

Create a `.env` file in the project folder and add your OpenAI API key:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

## Run the Application

### Streamlit Web App

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal.

### Command-Line Agent

```bash
python agent.py
```

Type your questions in the terminal, for example:

- Show all employees
- Find employees from IT
- Who has the highest salary?
- Add Rahul as an IT employee with salary 55000
- Delete employee 3
- Update employee 1 salary to 65000

## Example Queries

- "Show all employees."
- "How many employees are there?"
- "Find employees from Kolkata."
- "Find employees earning between 40000 and 60000."
- "Add Riya as a Marketing employee with salary 47000."
- "Update employee 2 city to Mumbai."
- "Delete employee 5."

## Database Schema

The SQLite table is named `employees` and contains the following columns:

- `id` — integer primary key
- `name` — employee name
- `email` — unique email address
- `department` — department name
- `salary` — employee salary
- `city` — employee city

## Notes

- Email addresses must be unique.
- The application uses OpenAI function calling to safely perform database actions.
- Destructive operations such as delete are only executed when the request clearly identifies the employee.

## License

This project is for educational and demonstration purposes.
