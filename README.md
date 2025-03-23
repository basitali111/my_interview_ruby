# RoR Intern Tasks

This repository contains my solutions for the following tasks:

1. **Add a Custom Route (`/about`)**  
2. **Set Up a Model with Associations (Author → Post)**  
3. **Prepare for Deployment (Heroku or Other Platforms)**

---

## 1. Getting Started

### Prerequisites
- **Ruby** (3.x or later)
- **Rails** (7.x or later)
- **PostgreSQL** (Version 9.3 and up)
- **Git**

### Installation

1. **Clone the repository**  
   ```bash
   git clone https://github.com/basitali111/my_interview_app.git
   ```
   Navigate into the project folder:
   ```bash
   cd my_interview_app
   ```

2. **Install Dependencies**  
   ```bash
   bundle install
   ```

3. **Database Configuration**

   By default, this application is configured to use PostgreSQL with the following settings in `config/database.yml`:

   ```yml
   default: &default
     adapter: postgresql
     encoding: unicode
     username: basit
     password: basit
     pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>

   development:
     <<: *default
     database: my_interview_app_development

   test:
     <<: *default
     database: my_interview_app_test

   production:
     <<: *default
     database: my_interview_app_production
     username: my_interview_app
     password: <%= ENV["MY_INTERVIEW_APP_DATABASE_PASSWORD"] %>
   ```

   - For **development** and **test** environments, the default username and password are `basit` / `basit`.
   - For **production**, the default username is `my_interview_app`, and the password is retrieved from the environment variable `MY_INTERVIEW_APP_DATABASE_PASSWORD`.  
   
   **Important:** Update these credentials to match your local PostgreSQL setup. If you prefer different credentials, open `config/database.yml` and change the `username` and `password` fields accordingly.

4. **Create and Migrate the Database**
   ```bash
   rails db:create
   rails db:migrate
   ```

5. **Run the Application**  
   ```bash
   rails server
   ```
   Open your browser at [http://localhost:3000](http://localhost:3000) to view the application.

---

## 2. Custom Route: `/about`

- A custom route `/about` has been added, leading to a static "About Us" page.
- This page is styled with **Bootstrap**.

To access the page, visit:  
```
http://localhost:3000/about
```

---

## 3. Model with Associations

- **Author** model: `has_many :posts, dependent: :destroy`
- **Post** model: `belongs_to :author`
- Deleting an Author automatically deletes their Posts.

### Example

```ruby
# app/models/author.rb
class Author < ApplicationRecord
  has_many :posts, dependent: :destroy
end

# app/models/post.rb
class Post < ApplicationRecord
  belongs_to :author
end
```

---

## 4. Deployment Preparation

### Why It’s Not Deployed to Heroku
- Heroku’s free tier is no longer available..

---

## Feedback or Changes

If you need any additional clarifications or modifications, please don’t hesitate to let me know. I’m open to revisiting any part of this solution to better match your requirements.

**Thank you!**
```
