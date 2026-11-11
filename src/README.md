# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities
- Persist activities and signups in a local SQLite database

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. From the `src` directory, run the application:

   ```
   uvicorn app:app --reload
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

The SQLite database is created as `src/activities.db` on first launch and is
seeded with the default activities and participants. Set the
`ACTIVITIES_DB_PATH` environment variable to store the database at a different
location.

## API Endpoints

| Method | Endpoint                                                           | Description                                                        |
| ------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| GET    | `/activities`                                                      | Get all activities and their participants                          |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu`  | Sign up for an activity                                             |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister from an activity                                      |

## Data Model

The SQLite database stores activities and their participants in separate
tables. Existing activity data is seeded only when the database is empty, so
subsequent application restarts preserve signups.
