# Rule Engine with Abstract Syntax Tree (AST)

## Project Overview

This project is a 3-tier rule engine application designed to evaluate user eligibility based on various attributes such as age, department, income, and spending. The system uses an Abstract Syntax Tree (AST) to represent conditional rules, allowing dynamic creation, combination, and modification of these rules. The application consists of a simple UI, API, and backend storage using SQLite for rule persistence.

## Features

- **Dynamic Rule Creation**: Create complex rules and store them as AST structures.
- **Rule Combination**: Combine multiple rules into a single AST efficiently.
- **Rule Evaluation**: Evaluate rules against user data (e.g., age, department) to determine eligibility.
- **AST Modification**: Modify existing ASTs by adding or removing conditions.
- **Database Integration**: Uses SQLite to store rules and their ASTs.
- **Error Handling**: Handles invalid rules, invalid data formats, and other errors gracefully.

## Design Choices

### 1. **Abstract Syntax Tree (AST)**
   - Each rule is converted into an AST to enable structured evaluation and dynamic modification.
   - The tree nodes represent either logical operators (AND, OR) or operand conditions (e.g., age > 30).
   - AST allows modular and scalable rule management with complex logic evaluation.

### 2. **SQLite Database**
   - Chosen for simplicity and ease of integration with the Python ecosystem. The rules and ASTs are stored as JSON objects for easy retrieval and manipulation.

### 3. **REST API with Flask**
   - A RESTful API was implemented using Flask to expose endpoints for rule creation, evaluation, and management.
   - SQLAlchemy is used to manage database interactions in an ORM style, providing an easy-to-use interface for storing and retrieving rules.

### 4. **Dockerization**
   - Docker is used to containerize the application, allowing for consistent and easy deployment. The Docker image includes both the Flask API and the SQLite database, ensuring the application can run seamlessly on any platform.

## Getting Started

### Prerequisites

- **Python 3.x**: Required for running the application.
- **Docker**: Optional but recommended for running the application in a containerized environment.

### Dependencies

To install the necessary dependencies, run the following command:

pip install -r requirements.txt

The main dependencies include:

Flask: Web framework for building the REST API.
SQLAlchemy: ORM for interacting with the SQLite database.
Regex: For validating rule strings.

## Database Setup
The project uses SQLite as the database to store rules and their ASTs. The database schema is automatically generated during the first run of the application.

You can also initialize the database manually by running:
python setup_database.py
This will create the necessary tables in the SQLite database.

## Running the Application Locally
### 1.Clone the repository:
git clone <repository_url>
cd <project_directory>
### 2. the dependencies:
pip install -r requirements.txt
### 3.Set up the database:
python setup_database.py
### 4.Start the Flask server:
python main.py
### 5.Access the API 

## API Documentation
### Endpoints
### 1.Create Rule
POST /create_rule
Accepts a rule string, converts it into an AST, and stores it in the database.
Example Request:
{
  "rule": "((age > 30 AND department = 'Sales') OR (age < 25 AND department = 'Marketing')) AND (salary > 50000 OR experience > 5)"
}
Example Response:
{
  "message": "Rule created successfully",
  "rule_id": 1
}
### 2.Combine Rules
POST /combine_rules
Combines multiple rules into a single AST.
Example Request:
{
  "rules": ["rule1", "rule2"]
}

### 3.Evaluate Rule
POST /evaluate_rule
Evaluates a rule against a user's data.
Example Request:
{
  "rule_id": 1,
  "data": {
    "age": 35,
    "department": "Sales",
    "salary": 60000,
    "experience": 3
  }
}

### 4.Modify Rule
PUT /modify_rule
Allows modification of an existing rule's AST.

### 5.Get All Rules
GET /rules
Fetches all stored rules along with their AST representations.

## Error Handling
The system has comprehensive error handling for:

Invalid rule strings (e.g., missing operators, invalid comparisons).
Invalid JSON data formats.
Rule modification errors.

## Running Tests
You can run the test cases to verify the functionality of the rule engine
python test_rule_engine.py
The tests include:
Validation of AST creation for individual rules.
Rule combination testing.
Rule evaluation with various user datasets.
Error handling tests for invalid rule strings and data.

## Build Instructions
To build and run the project:

Ensure you have Python 3.x installed.
Clone the repository and navigate to the project directory.
Install dependencies using pip install -r requirements.txt.
Set up the database using python setup_database.py.
Run the Flask server using python main.py.
(Optional) Use Docker to containerize and run the application.

## Docker Setup
The application is fully containerized using Docker. The Docker setup includes the following services:

Flask API: Exposes the REST endpoints.
SQLite Database: Stores the rules and their ASTs.

