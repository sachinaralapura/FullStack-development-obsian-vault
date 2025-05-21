---
tags:
  - mongodb
---

```js
{
  "college_db": {
    "students": [
      {"_id": 1, "name": "Alice Smith", "age": 20, "major": "Computer Science", "gpa": 3.8, "city": "New York", "enrolled": true, "courses": ["CS101", "MATH201"], "graduation_year": 2026},
      {"_id": 2, "name": "Bob Johnson", "age": 22, "major": "Physics", "gpa": 3.2, "city": "Boston", "enrolled": true, "courses": ["PHY101", "MATH202"], "graduation_year": 2025},
      {"_id": 3, "name": "Cathy Lee", "age": 19, "major": "Biology", "gpa": 3.9, "city": "Chicago", "enrolled": true, "courses": ["BIO101", "CHEM101"], "graduation_year": 2027},
      {"_id": 4, "name": "David Kim", "age": 21, "major": "Mathematics", "gpa": 3.5, "city": "Los Angeles", "enrolled": false, "courses": ["MATH301"], "graduation_year": 2024},
      {"_id": 5, "name": "Emma Brown", "age": 20, "major": "Chemistry", "gpa": 3.7, "city": "Seattle", "enrolled": true, "courses": ["CHEM201", "BIO102"], "graduation_year": 2026}
    ],
    "courses": [
      {
        "_id": "CS101",
        "title": "Introduction to Programming",
        "credits": 3,
        "department": "Computer Science",
        "instructor_id": 101,
        "schedules": [
          {"day": "Monday", "time": "10:00-11:30", "room": "CS101-A"},
          {"day": "Wednesday", "time": "10:00-11:30", "room": "CS101-A"},
          {"day": "Friday", "time": "14:00-15:00", "room": "CS101-Lab"}
        ]
      },
      {
        "_id": "MATH201",
        "title": "Calculus I",
        "credits": 4,
        "department": "Mathematics",
        "instructor_id": 102,
        "schedules": [
          {"day": "Tuesday", "time": "13:00-14:30", "room": "MATH201-B"},
          {"day": "Thursday", "time": "13:00-14:30", "room": "MATH201-B"},
          {"day": "Monday", "time": "15:00-16:00", "room": "MATH201-Tut"}
        ]
      },
      {
        "_id": "PHY101",
        "title": "General Physics",
        "credits": 3,
        "department": "Physics",
        "instructor_id": 103,
        "schedules": [
          {"day": "Monday", "time": "14:00-15:30", "room": "PHY101-C"},
          {"day": "Wednesday", "time": "14:00-15:30", "room": "PHY101-C"},
          {"day": "Thursday", "time": "16:00-17:00", "room": "PHY101-Lab"}
        ]
      },
      {
        "_id": "BIO101",
        "title": "Introductory Biology",
        "credits": 3,
        "department": "Biology",
        "instructor_id": 104,
        "schedules": [
          {"day": "Tuesday", "time": "09:00-10:30", "room": "BIO101-D"},
          {"day": "Thursday", "time": "09:00-10:30", "room": "BIO101-D"},
          {"day": "Friday", "time": "11:00-12:00", "room": "BIO101-Lab"}
        ]
      },
      {
        "_id": "CHEM201",
        "title": "Organic Chemistry",
        "credits": 4,
        "department": "Chemistry",
        "instructor_id": 105,
        "schedules": [
          {"day": "Monday", "time": "11:00-12:30", "room": "CHEM201-E"},
          {"day": "Wednesday", "time": "11:00-12:30", "room": "CHEM201-E"},
          {"day": "Tuesday", "time": "14:00-15:30", "room": "CHEM201-Lab"}
        ]
      }
    ],
    "instructors": [
      {"_id": 101, "name": "Dr. Jane Doe", "department": "Computer Science", "email": "jane.doe@college.edu", "office": "CS Building 101", "courses_taught": ["CS101"]},
      {"_id": 102, "name": "Dr. John Smith", "department": "Mathematics", "email": "john.smith@college.edu", "office": "Math Building 202", "courses_taught": ["MATH201"]},
      {"_id": 103, "name": "Dr. Emily Chen", "department": "Physics", "email": "emily.chen@college.edu", "office": "Physics Lab 303", "courses_taught": ["PHY101"]},
      {"_id": 104, "name": "Dr. Michael Brown", "department": "Biology", "email": "michael.brown@college.edu", "office": "Bio Building 404", "courses_taught": ["BIO101"]},
      {"_id": 105, "name": "Dr. Sarah Lee", "department": "Chemistry", "email": "sarah.lee@college.edu", "office": "Chem Lab 505", "courses_taught": ["CHEM201"]}
    ],
    "departments": [
      {"_id": "CS", "name": "Computer Science", "head": 101, "building": "CS Building", "budget": 500000},
      {"_id": "MATH", "name": "Mathematics", "head": 102, "building": "Math Building", "budget": 300000},
      {"_id": "PHY", "name": "Physics", "head": 103, "building": "Physics Building", "budget": 400000},
      {"_id": "BIO", "name": "Biology", "head": 104, "building": "Bio Building", "budget": 350000},
      {"_id": "CHEM", "name": "Chemistry", "head": 105, "building": "Chem Building", "budget": 450000}
    ]
  }
}
```
