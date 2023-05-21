# Technical ReadMe: Conducting Technical Audits

## Introduction
This repository contains the source code for the technical auditing platform for conducting technical audits to identify and mitigate challenges. This platform improves the platform performance by taking action based on the results of periodic audits.

## Architecture
The project is structured as a Flask web application, which exposes an API for both scheduled and trigger-based audits to run. These APIs provide the required performance, security, and technology recommendations. It also integrates with various low-level software components that facilitate the audit process, including:

- psutil - A cross-platform library for retrieving system metrics
- datetime - A module  for performing date and time calculations
- SQLAlchemy - A Python SQL toolkit for interacting with databases

## Database Schema
The system's architecture makes use of an SQL database to store the metric and auditing data. Here are the database schema and models that will exist in the system:

### Metrics
| Name      | Type    | Constraints |
|-----------|---------|-------------|
| id        | int     | PRIMARY KEY |
| timestamp | datetime| NOT NULL    |
| metric    | varchar| NOT NULL    |
| value     | int     | NOT NULL    |

### Audits
| Name        |Type     | Constraints |
|-------------|---------|-------------|
| id          |int      | PRIMARY KEY |
| start_time  |datetime | NOT NULL    |
| end_time    |datetime | NOT NULL    |
| recommendations|jsonb | NOT NULL    |

### Security Recommendations
| Name        |Type     | Constraints |
|-------------|---------|-------------|
| id          |int      | PRIMARY KEY |
| audit_id    |int      | REFERENCES audits.id |
| message     |varchar |NOT NULL     |
| action      |varchar |NOT NULL     |
| parameter   |varchar |NOT NULL     |

### Performance Optimization Recommendations
| Name        |Type     | Constraints |
|-------------|---------|-------------|
| id          |int      | PRIMARY KEY |
| audit_id    |int      | REFERENCES audits.id |
| message     |varchar |NOT NULL     |
| action      |varchar |NOT NULL    |
| parameter   |varchar |NOT NULL     |

### Deprecated Technologies Recommendations
| Name        |Type     | Constraints |
|-------------|---------|-------------|
| id          |int      | PRIMARY KEY |
| audit_id    |int      | REFERENCES audits.id |
| technology  |varchar |NOT NULL     |
| reason      |varchar |NOT NULL    |

The database schema will use JSONB format to store all the recommendations made by the system, making it highly flexible but also fast to retrieve data.

## Installation

### Prerequisites
Ensure you have the following installed:
 - Python3.8+
 - pip3
 - PostgresSQL (or any other suitable DB)

### Steps
1. Clone the repository `https://github.com/<username>/technical-auditing-platform.git`
2. Navigate into the project folder `cd technical-auditing-platform`
3. Create and activate a virtual environment by entering `virtualenv venv && source venv/bin/activate` on the terminal.
4. Install project dependencies with `pip3 install -r requirements.txt`
5. Export the following environment variables:
   - `DATABASE_URL` - URL path to the Postgres database instance to be used.
6. Start the development server `export FLASK_ENV=development && flask run`

### Project Structure
    ├── app
    │   ├── __init__.py
    │   ├── audit
    │   │   ├── __init__.py
    │   │   └── service.py
    │   ├── database.py
    │   ├── performance
    │   │   ├── __init__.py
    │   │   └── service.py
    │   ├── schema.sql
    │   ├── security
    │   │   ├── __init__.py
    │   │   └── service.py
    │   ├── tech
    │   │   ├── __init__.py
    │   │   └── service.py
    │   └── views
    │        ├── __init__.py
    │        ├── audit.py
    │        ├── dashboard.py
    │        └── schedule.py
    ├── configs
    │   ├── __init__.py
    │   └── config.py
    ├── env.sample
    ├── README.md
    ├── requirements.txt
    └── run.py

## Endpoints and Functionality
The project has the following endpoints:
- `/` - The application root.
- `/dashboard` - The page displays graphs of the different metrics that the system has recorded in the database for the system’s performance.
- `/recommendations` - The page displays performance, security, and technology recommendations that the system made in its latest audit
- - `/recommendations/performance` - Returns a list of optimization recommendations that the system made.
- `/recommendations/security` - Returns a list of security recommendations that the system made.
- `/recommendations/technology` - Returns a list of deprecated technologies that the system detected.

### Endpoint URL Parameters For Scheduling Audits
- `/schedule?type=<audit_type>&interval=<time_interval_in_seconds>` - Schedules a regular audit of the specified type (performance, security, or technology). The time interval specifies how frequently the audit will run.

### API Documentation
For details on the endpoints' API documentation, follow the path `/api/v1/documentation`.


## Conclusion
We have developed an application for conducting technical audits of a system, providing performance, security, and technology recommendations based on the audit results. The project's code is structured and follows the best industry practices, including the use of a virtual environment, a modern web framework, SQLAlchemy, and a high-level project structure.

The repo's file structure is logically organized, making it easy to navigate and switch between different components of the project. I hope this guide helps you get started with the platform quickly and easily.

Contributions to this repository are welcome and encouraged.
