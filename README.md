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

```bash
pip install -r requirements.txt
