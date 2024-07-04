## ClaClo - CMS Fastapi 


## Table of Contents

1. [Overview & Requirements](#overview-&-requirements)
1. [Running Locally](#running-the-app-locally)
1. [Tech Stack](#tech-stack)
1. [Schema]

This is a content management application where administrators can manage students and students can see their courses.

## Overview & Requirements
- Administrators can perform CRUD operations on students.
- Administrators can create courses with sections and content blocks in each section.

- Future Work
- Administrators can assign courses to students.
- Students and Teachers can interact view their courses in a list.
- Students and Teachers can see the sections and content blocks for individual courses that they are taking.
- Students are able to see their progress for each course.

## Running the App Locally

Setup env
```
virtualenv venv
```
For Linux/Mac
```
source venv/bin/activate
```
For Windows
```
source venv/Scripts/activate
```
Install package
```
pip install fastapi pymongo uvicorn
```
Start server 
```
uvicorn index:app --reload

## Tech Stack

- Fast API
- Python 3.9+
- Mongodb Atlas
- Pydantic


## Schema

**User**

"id": str(item["id"]),
        "name": item["name"],
        "email": item["email"],
        "password": item["password"]


## Future Work

**Profile**

- first_name: str
- last_name: str
- bio: str (TextField)
- user_id: fk

**Course**

- title: str
- description: str (TextField)
- user_id: fk

**Section**

- title
- description
- course_id

**ContentBlock**

- title
- description
- type
- url
- content
- section_id

**StudentCourse**

*This model is used for teachers to assign courses to students. The 'completed' boolean is False until the student has completed the whole course.*

- student_id
- course_id
- completed

**CompletedContentBlock**

*Every time the student completes a content block, a row is created in this table. The teacher can then go and edit this information when they grade the content block and provide feedback.*

- student_id
- content_block_id
- url
- feedback
- grade
