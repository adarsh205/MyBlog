# MyBlog

This is a blog application built with Python, Flask, and PostgreSQL. The application allows users to view blog posts, comment on them, and features an admin system for managing blog content.
You can visit the website [Here](https://myblog-0tkv.onrender.com)

## Features

- **Admin functionality**: Only admins can create and delete blog posts.
- **User registration and login**: Users can sign up, log in, and comment on blog posts.
- **Blog posts**: Users can view all blog posts. Admins can create, update, and delete posts.
- **Comments**: Logged-in users can comment on blog posts.
- **Password Security**: Passwords are hashed and salted using `Werkzeug` for security.

## Tech Stack

- **Backend**: Python, Flask
- **Database**: PostgreSQL (Relational DB with 3 tables: `BlogPosts`, `Users`, and `Comments`)
- **Authentication**: User login functionality with Flask and `Werkzeug` for password hashing and salting.
- **ORM**: SQLAlchemy for database interaction

## Database Schema

- ### Users Table:
  - `id` (Primary Key)
  - `name` 
  - `email` 
  - `password` (Hashed and salted using `Werkzeug`)
  - **Relationships**:
    - `posts` (One-to-Many relationship with `BlogPost`)
    - `comments` (One-to-Many relationship with `Comments`)

- ### BlogPosts Table:
  - `id` (Primary Key)
  - `title` 
  - `subtitle` 
  - `date` 
  - `body` 
  - `img_url` 
  - `author_id` (Foreign Key to Users table)
  - **Relationships**:
    - `author` (Many-to-One relationship with `Users`)
    - `comments` (One-to-Many relationship with `Comments`)

- ### Comments Table:
  - `id` (Primary Key)
  - `comment` 
  - `commenter_id` (Foreign Key to Users table)
  - `blog_id` (Foreign Key to BlogPosts table)
  - **Relationships**:
    - `commenter` (Many-to-One relationship with `Users`)
    - `blog` (Many-to-One relationship with `BlogPosts`)

## Setup Instructions

### Prerequisites

- Python 3.x
- PostgreSQL
- Flask
- SQLAlchemy
- Werkzeug
- Virtual environment (optional but recommended)

### Installation Steps

1. **Clone the repository**:

    ```bash
    git clone https://github.com/adarsh205/MyBlog.git
    cd MyBlog
    ```

2. **Create a virtual environment** (optional but recommended):

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up PostgreSQL database**:
    - Create a PostgreSQL database for the project.
    - Update the `config.py` file with your PostgreSQL credentials.

5. **Set up Environment Variables**:
   - Set up your `SECRET_KEY` in a `.env` file

6. **Initialize the database**:

    ```bash
    flask db init
    flask db migrate
    flask db upgrade
    ```

7. **Run the application**:

    ```bash
    flask run
    ```

8. Visit `http://127.0.0.1:5000` in your browser to view the app.


## User Roles

- **Admin**:
  - Can create, edit, and delete blog posts.
  - Can view and delete any user comments.
  
- **Logged-in users**:
  - Can comment on blog posts.
  - Can view all blog posts and comments.
  
- **Non-logged-in users**:
  - Can view blog posts but cannot comment or create posts.


