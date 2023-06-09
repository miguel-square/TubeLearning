# Overview

Is a dashboard where you can import youtube videos of courses to follow along taking notes, saving progress, organize them in shareable learning paths, rate them (and even code along in the case of dev courses). One of the main advantages is to have the video stripped of all the distractions of youtube.

## Problem Definition

Sometimes is hard to follow along a video when is surrounded by secondary information, comments, suggestions, etc. Also, within YouTube you can organize the videos in playlists but they are limited if you want to create a personalized learning path.  

## Priorities

### Must have

- A user must be able to sign up and login
- A user must be able to import and embedded YouTube video from an url
- A user must be able to create a learning path
- A user must be able to create a course that could be related to a learning path
- A user must be able to write and save notes in the course

### Should have

- A user should be able to save the current course progress
- A user should be able to rate a course 
- A user should be able to list its courses by rating 

### Could have

- A user could open an embedded code enviroment and code along with the video
- A user could search for a YouTube video within the app
- A user could set weekly and monthly learning goals.

### Will not have

- Embeds form other platforms

## Domain diagram 

```mermaid
erDiagram
    User }o--|| LearningPath : creates
    User }o--|| Course : creates
    LearningPath }o--o{ Course: has
    Course |o--|| Notes: has
    Course ||--|{ Video: has
```

### Entity Relationship Diagram

```mermaid
%%{init: {'theme':'dark'}}%%
erDiagram
    User }o--|| LearningPath : creates
    User {
        int id PK
        text username
        text first_name
        text second_name
        text password
    }
    User }o--|| Course : creates
    Course {
        int id PK
        text name
        text description
        int rating
        int user_id FK
        int path_id FK
    }
    LearningPath }o--o{ Course: has
    LearningPath {
        int id PK
        text name
        text description
        int rating
        int user_id FK
    }
    Course |o--|| Notes: has
    Notes {
        int id PK
        text content
        int course_id FK
    }
    Course ||--|{ Video: has
    Video {
        int id PK
        text url
        int time
        int course_id FK
    }

```
