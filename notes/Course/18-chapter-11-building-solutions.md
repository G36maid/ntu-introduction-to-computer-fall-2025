# Building Solutions: Database, System, and Application Development Tools

**DISCOVERING COMPUTERS 2018: Digital Technology, Data, and Devices - Module 11**

## Objectives Overview
1.  Databases, Data, and Information.
2.  File Processing Systems and Databases.
3.  Database Management Systems (DBMS).
4.  System Development.
5.  Application Development Languages.

## Databases, Data, and Information

### Data vs. Information
*   **Data**: Collection of unprocessed items (Text, Numbers, Images, Audio, Video).
*   **Information**: Processed data that is organized, meaningful, and useful.

| Characteristic | Data | Information |
| :--- | :--- | :--- |
| **Form** | Raw, unprocessed | Processed and organized |
| **Value** | Lacks inherent value | Has value to user/context |
| **Dependency** | Independent | Depends on data |
| **Example** | 30°C | "Today is warmer than yesterday" |

### Hierarchy of Data
Data is organized in levels:
1.  **Character**: One byte (number, letter, symbol).
2.  **Field**: A combination of related characters (e.g., Instructor ID). Has Field Name, Size, and Type.
3.  **Record**: A group of related fields (e.g., one instructor's details).
    *   **Primary Key**: A field that uniquely identifies each record.
    *   **Foreign Key**: A field that refers to the primary key of another table, linking them.
4.  **Data File**: A collection of related records.
5.  **Database**: Collection of data organized for access, retrieval, and use.

### Data Maintenance and Validation
**File Maintenance**: Adding, Modifying, and Deleting records.

**Validation** compares data with a set of rules:
*   **Alphabetic/Numeric check**: Ensures correct format.
*   **Range check**: Ensures data is within limits.
*   **Consistency check**: Ensures logic between fields (e.g., Check-out date > Check-in date).
*   **Completeness check**: Ensures no missing critical info.
*   **Check digit**: Mathematical calculation to verify accuracy (e.g., ID card numbers).

## File Processing Systems vs. Databases

### File Processing System
*   Each department has its own files.
*   **Issues**: Redundant data, Isolated data (Data Silos).

### Database Approach
*   Programs and users share data.
*   **Benefits**: Reduced redundancy, Improved integrity, Shared data, Easier access.
*   **Disadvantages**: More complex, requires more memory/processing power, centralized vulnerability.

### Big Data & Risks
*   **Data Creep**: Unintentional collection, Over-retention, Scope expansion.

### Data Models
*   **Relational Database**: Stores data in tables; most common.
*   **Object-Oriented Database (OODB)**: Stores data in objects.
*   **Data Dictionary**: Contains metadata (definitions) about each file and field.

## Database Management Systems (DBMS)
Software that allows users to create, access, and manage a database (e.g., SQL Server, Oracle).

### Tools
*   **Query Language**: English-like statements to retrieve/update data.
    *   **SQL (Structured Query Language)**: Standard language for relational databases (SELECT, FROM, WHERE).
*   **Query By Example (QBE)**: GUI tool to assist in retrieving data.
*   **Form**: Window for entering/modifying data.
*   **Report Writer**: Designs and prints reports.

### Security and Maintenance
*   **Access Privileges**: Defines who can access what.
*   **Principle of Least Privilege**: Users/programs are given only the minimum permissions necessary.
*   **Backup and Recovery**: Log, Recovery utility, Continuous backup.

## System Development (SDLC)
**System Development Life Cycle (SDLC)** is a set of activities used to build an information system.

### Phases
1.  **Planning**: Review requests, prioritize projects, allocate resources, form team.
2.  **Analysis**:
    *   **Preliminary Investigation**: Determine problem nature.
    *   **Detailed Analysis**: Study current system, determine requirements.
    *   **System Proposal**: Buy retail, Build custom, Outsource, etc.
3.  **Design**:
    *   Acquire hardware/software.
    *   Develop details (Mock-ups, Layout charts).
4.  **Implementation**:
    *   Develop programs.
    *   **Test**: Unit (individual), Systems (integrated), Integration (with other apps), Acceptance (actual data).
    *   **Train Users**.
    *   **Conversion**: Direct, Parallel, Phased, Pilot.
5.  **Support and Security**: Maintenance, Monitoring, Security assessment.

### Project Management
*   Elements: Scope, Activities, Time, Cost, Order.
*   **Gantt Chart**: Visualizes schedule (time-based).
*   **PERT Chart**: Visualizes dependencies and task sequence.
*   **Feasibility**: Operational, Schedule, Technical, Economic.

### Documentation & Gathering
*   **JAD (Joint-Application Design)**: Collaborative workshops.
*   **Documentation**: Essential for future maintenance.

## Application Development Languages

### Programming Languages
*   **Procedural Language**: Uses English-like words to tell computer *what* and *how* to do (e.g., C).
    *   **Compiler**: Converts entire source code to machine code before execution (Fast, creates .exe).
    *   **Interpreter**: Translates and executes one instruction at a time (Flexible, slower).
*   **Object-Oriented Programming (OOP)**: Implements objects (reusable). E.g., Java, C++, Visual Studio (.NET).
*   **4GL (Fourth-Generation Language)**: Nonprocedural access to data (e.g., SQL).
*   **Classic Languages**: BASIC, COBOL, FORTRAN (Legacy systems).

### Web Development
*   **HTML (Hyper-Text Markup Language)**: Formatting for web documents.
*   **XML (eXtensible Markup Language)**: Describes structure of information.
*   **WML**: Wireless Markup Language.
*   **Scripting Languages**: JavaScript (Client-side interactivity), Perl, PHP, Python, Ruby.

### Other Tools
*   **Application Generator**: Creates code from specifications.
*   **Macro**: Automated series of statements (Record or Write).

## Homework (Due Dec. 29, 2025)
**Access Project**:
1.  Input a list of three friends (Name, Email, Phone, Address, Birthday).
2.  Design a Christmas card.
3.  Send the card via email to each friend.
4.  Use Mail Merge to print the card and envelope for each friend.