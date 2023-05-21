# Technical Software Spec: Conducting Technical Audits

### Introduction
This technical software spec outlines the development of a platform that can conduct technical audits to identify and mitigate challenges on a system, thereby improving the platform's efficiency. 

### System Architecture
The platform will consist of two primary components:
- The audit engine, which will perform the technical audit
- The web interface, which will allow the users to interact with the platform

These two primary components will be built using the following technologies and tools:
- Python 3.8+ programming language 
- Flask as the web framework 
- SQLAlchemy as the ORM

### Functionality
The system will have the following features:
1. Ability to retrieve the system metrics such as memory utilization, CPU utilization, Disk usage, etc.
2. Ability to view the list of audits that have been completed on a given platform with detailed reports.
3. Ability to schedule audits that can run autonomously with different time configurations
4. Locate potential security issues and make recommendations for improving the system’s security
5. Identify Bottlenecks and suggest steps to optimize the system performance
6. Will report outdated and deprecated technologies that should be removed to improve the system,

### Database
The system will make use of a database that contains information about the executed audits. The database will use SQLAlchemy(Can use any other suitable ORM) as an ORM to interact with the database.

The database's schema will consist of the following tables:
- Metrics - This table will store information such as Memory utilization, CPU utilization, Disk usage, etc. 
- Audit - This table will store information about the audit such as start time, end time, and all the recommendations.
- Security Recommendations - This table will keep security recommendations that the system made.
- Performance Optimization Recommendations - This table will keep optimization recommendations that the system made.
- Deprecated Technologies Recommendations- This table will store Technology that has been deprecated

### Audit Process
The following audit process will be implemented:
1. The system retrieves the required system metric from the server.
2. The system checks for security issues, optimizations, and deprecated technologies.
3. Recommendations would be displayed on the system's dashboard.
4. Saves all the recommendations to the audit tables in the database.

### Web Interface
The platform's web interface will be developed using Python Flask framework to provide an intuitive way for the user to interact with the audit system. The interface will provide the following functionality:
1. Ability to view the list of completed audits
2. Ability to see detail reports of every audit
3. Ability to schedule audits and view scheduling history

The Web interface will have the following endpoints:
1. `/` - The homepage
2. `/audits` - This page will provide a list of completed audits, with some key information about each audit, such as audit ID, timestamp, and number of recommendations.
3. `/audits/<audit_id>` - This page will display a detailed report of a specific audit, including all recommendations that the system made.
4. `/schedule` - The page will allow the user to schedule recurring audits.

### Conclusion
The platform will be created with reliable foundations. When implemented, the system will have the ability to conduct technical audits autonomously with different time configurations, making recommendations to optimize the platform's performance, locate potential security vulnerabilities, and suggest steps to remove deprecated technology. Nonetheless, this is just the first pass, and there will be improvements to follow. 

`build`, let's get started!
