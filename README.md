# RaceDay – Part 1

## Project Overview

RaceDay is an event management system designed for running, walking and cycling events in South Africa.

The system is designed to help event organisers manage events, categories, participant enrolments and results in one organised system.

The project addresses problems that can occur when event information is managed using paper forms, spreadsheets and separate communication channels.

---

## Problem Statement

Many road events use different methods to manage registrations, participant information, event categories and results.

This can result in:

* Duplicate or incorrect information
* Difficulties managing participants
* Information being stored in different places
* Difficulty tracking results
* More administrative work for event organisers

RaceDay aims to provide a structured database and planned API that can support these activities.

---

## User Roles

RaceDay has two main user roles.

### Organiser

The Organiser manages the events.

The Organiser can:

* Create events
* Edit events
* Delete events
* Manage event categories
* View participant enrolments
* Capture participant results
* Manage event information

### Participant

The Participant takes part in events.

The Participant can:

* Create an account
* Log in
* Browse events
* View event categories
* Enter an event category
* View their enrolments
* Track their results

---

# Part 1 Objectives

The main objectives of Part 1 are to plan and design the RaceDay system before developing the REST API and MVC application.

Part 1 includes:

1. Entity Relationship Diagram
2. API Endpoint Plan
3. SQL Database
4. Sample Data
5. Project Documentation

---

# Database Design

The RaceDay database contains the following main entities:

| Entity          | Purpose                               |
| --------------- | ------------------------------------- |
| Users           | Stores organisers and participants    |
| Events          | Stores event information              |
| Categories      | Stores event categories and distances |
| EventCategories | Connects events with categories       |
| Enrolments      | Stores participant event entries      |
| Results         | Stores participant results            |
| Routes          | Stores route information              |
| Weather         | Stores event weather information      |

---

# Important Relationships

The database uses primary keys and foreign keys to connect the entities.

### Users → Events

One organiser can manage many events.

**Cardinality:** 1:M

### Users → Enrolments

One participant can have many enrolments.

**Cardinality:** 1:M

### Events → EventCategories

One event can have many event categories.

**Cardinality:** 1:M

### Categories → EventCategories

One category can be used for many events.

**Cardinality:** 1:M

### EventCategories → Enrolments

One event category can have many participants.

**Cardinality:** 1:M

### Enrolments → Results

An enrolment can have zero or one result.

**Cardinality:** 1:0..1

### Events → Routes

An event can have zero or one route.

**Cardinality:** 1:0..1

### Events → Weather

An event can have multiple weather records.

**Cardinality:** 1:M

---

# API Endpoint Plan

The API plan describes how the future RaceDay REST API will communicate with the database and application.

The main API areas are:

* Authentication and Users
* Events
* Event Categories
* Event Enrolments
* Results
* Routes
* Weather

The API endpoint plan can be found in:

```text
docs/API_Endpoint_Plan.md
```

The endpoint plan includes:

* HTTP Method
* Endpoint/Route
* Who Can Use
* What It Does
* Request Body
* Expected Response

---

# Example API Endpoints

### Authentication

```text
POST /api/auth/register
POST /api/auth/login
```

These endpoints will allow users to create accounts and log into the system.

### Events

```text
GET /api/events
POST /api/events
GET /api/events/:id
PATCH /api/events/:id
DELETE /api/events/:id
```

These endpoints will allow events to be viewed and managed.

### Enrolments

```text
POST /api/enrolments
GET /api/enrolments
GET /api/enrolments/:id
DELETE /api/enrolments/:id
```

These endpoints will manage participant enrolments.

### Results

```text
POST /api/results
PATCH /api/results/:id
GET /api/results/:id
```

These endpoints will be used to manage and view participant results.

---

# SQL Database

The SQL database script is located in:

```text
database/RaceDay.sql
```

The script creates the RaceDay database and its tables.

It also:

* Creates primary keys
* Creates foreign keys
* Adds unique constraints
* Adds validation constraints
* Inserts sample data
* Runs verification queries

---

# Sample Data

The database includes sample data for testing the structure.

The sample data includes:

* Organisers
* Participants
* Events
* Categories
* Event categories
* Enrolments
* Results
* Routes
* Weather records

This allows the database relationships to be tested before the API is developed.

---

# ERD

The Entity Relationship Diagram is located at:

```text
docs/RaceDay_ERD.png
```

The ERD shows the entities, attributes, primary keys, foreign keys and relationships used in the RaceDay database.

---

# Project Folder Structure

```text
RaceDay/
│
├── .github/
│   └── workflows/
│
├── docs/
│   ├── 00_READ_ME_FIRST.md
│   ├── RaceDay_ERD.png
│   ├── API_Endpoint_Plan.md
│   ├── ERD_Entity_Specification.md
│   ├── Part1_Submission_Checklist.md
│   └── AI_Disclosure.md
│
├── database/
│   └── RaceDay.sql
│
├── README.md
│
└── video/
    └── RaceDay_Part1_Video_Script.md
```

---

# How to Run the Database

## Step 1

Open **SQL Server Management Studio (SSMS)**.

## Step 2

Open:

```text
database/RaceDay.sql
```

## Step 3

Run the SQL script.

## Step 4

Check that the `RaceDayDB` database has been created.

## Step 5

Check the tables:

```text
Users
Events
Categories
EventCategories
Enrolments
Results
Routes
Weather
```

## Step 6

Run the SELECT queries included in the SQL script to confirm that the sample data was inserted successfully.

---

# Design Decisions

One important design decision was to separate `Events` and `Categories`.

An event can have different categories, and the same category can be used by different events.

Therefore, the `EventCategories` junction table was created to manage this relationship.

Another design decision was to separate `Enrolments` from `Results`.

A participant can enrol in an event before the event takes place. A result may only exist after the participant completes the event.

The `Users` table also contains the user's role so that the system can distinguish between Organisers and Participants.

---

# Part 1 Deliverables

The following documents should be included in the repository:

* ERD
* API Endpoint Plan
* SQL Database Script
* Entity Specification
* Submission Checklist
* AI Disclosure
* README
* Video Presentation Script

---

# AI Disclosure

AI tools were used during the planning and development process.

ChatGPT was used to help understand the assignment requirements, plan the database structure, organise the ERD, develop the API endpoint plan, explain SQL concepts, structure documentation and identify possible errors.

The AI output was reviewed and adapted as part of the project development. I am responsible for the final work submitted and for understanding the design and implementation decisions.

A detailed AI disclosure is available in:

```text
docs/AI_Disclosure.md
```

---

# Video Presentation

The Part 1 WILL explain:

1. The RaceDay problem
2. The two user roles
3. The ERD
4. Important relationships and cardinalities
5. The API endpoint plan
6. The SQL database structure
7. Sample data
8. Design decisions

The presentation script is available in:

```text
video/RaceDay_Part1_Video_Script.md
```

---

# Author

**Name:** Masibonge Mtshali

**Student Number:** ST10491925

**Module:** Programming 2B

**Project:** RaceDay – Part 1

---

# Conclusion

RaceDay Part 1 establishes the foundation for the system by defining the database structure, relationships, API requirements and system design.

The ERD and SQL database provide the data foundation, while the API endpoint plan provides a guide for developing the REST API in the next part of the project.
