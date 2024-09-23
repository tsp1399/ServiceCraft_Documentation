### Project Summary

#### Project Overview
This is a low-tech, low-scale Django-based platform aimed at managing WorkItems, collecting keyword data via APIs, and offering keyword and website analytics. The platform uses SQLite for local storage and includes a centralized API management system to handle external services like DataForSEO and OpenAI GPT.

#### Stack and Technologies
1. **Backend**: Django Framework with SQLite as the database.
2. **Frontend**: Bootstrap for responsive design and vanilla JavaScript for interactivity.
3. **APIs**:
   - DataForSEO for keyword analytics.
   - OpenAI GPT for NLP tasks and content generation.
4. **API Management**: A shared Django app for handling API calls across the project.

### Core Features
1. **WorkItems Management**:
   - Create and manage WorkItems (articles, deliverables) with associated tasks.
   - Kanban board for tracking task status with drag-and-drop functionality.
   - Filtering and searching by various attributes (e.g., user, status, date).

2. **Keyword Analytics**:
   - Gather keyword data for WorkItems from DataForSEO and store it in a dedicated model.
   - Display keyword insights such as search volume and competition.
   - Link keywords to WorkItems for content performance tracking.

3. **Personal Website Analytics**:
   - Display overall website traffic and a breakdown by source and device.
   - Visual sitemap for individual page performance analytics.

4. **Admin Portal**:
   - Manage users, roles, and permissions.
   - Monitor overdue tasks, alerts, and user activity.
   - Set preferences like themes and view user engagement analytics (e.g., A/B testing).

5. **Interactive Visual Sitemap** (Basic):
   - Visualize website structure and key performance metrics.
   - Clickable and interactive elements for exploring page performance.

### Core Apps

1. **`workitems`**:
   - **Purpose**: Manage WorkItems and tasks.
   - **Key Pages**:
     - Planner Page (kanban board for task management).
     - WorkItem Detail Page (individual WorkItem view).
   
2. **`analytics`**:
   - **Purpose**: Manage and display keyword and website analytics.
   - **Key Pages**:
     - Keyword Analytics Dashboard.
     - Individual Keyword Report.
     - Personal Website Analytics (sitemap, traffic breakdown).

3. **`admin_portal`**:
   - **Purpose**: Manage user roles, permissions, and notifications.
   - **Key Pages**:
     - User Management Dashboard.
     - Notification Logs.
     - Preferences.

4. **`api_client`**:
   - **Purpose**: Centralized API management for handling external API services like DataForSEO and OpenAI GPT.
   - **Components**:
     - Service classes for interacting with APIs.
     - Utility functions for common tasks like authentication and error handling.

5. **`homepage`**:
   - **Purpose**: Public-facing homepage with login and top 5 keywords.
   - **Key Pages**:
     - Index Page (company overview and top keywords).

### Folder and File Directory Structure

```
my_project/
│
├── manage.py
├── db.sqlite3
├── .env                         # Environment variables for API keys and settings
│
├── my_project/                  # Project configuration
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py                  # Main URL configuration
│   ├── wsgi.py
│   └── asgi.py
│
├── static/                      # Static files
│   ├── css/
│   │   └── bootstrap.min.css
│   ├── js/
│   │   └── main.js              # Global JavaScript file
│   └── images/
│
├── templates/                   # HTML templates
│   ├── base.html                # Base layout template
│   ├── index.html               # Public homepage
│   └── 404.html                 # Error page
│
├── workitems/                   # WorkItems management app
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py                # WorkItems and Tasks models
│   ├── views.py                 # Views for managing WorkItems
│   ├── urls.py                  # URL routing for workitems app
│   ├── templates/
│   │   └── workitems/
│   │       ├── planner.html     # Kanban view for tasks
│   │       ├── workitem_detail.html # Detailed WorkItem view
│   └── static/
│       ├── css/
│       │   └── workitems.css    # CSS for workitems app
│       └── js/
│           └── workitems.js     # JavaScript for kanban interactivity
│
├── analytics/                   # Keyword and website analytics app
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py                # Models for keyword and website analytics
│   ├── views.py                 # Views for analytics dashboards
│   ├── urls.py                  # URL routing for analytics app
│   ├── templates/
│   │   └── analytics/
│   │       ├── keyword_dashboard.html   # Keyword analytics dashboard
│   │       ├── keyword_report.html      # Individual keyword report
│   │       └── site_analytics.html      # Website analytics (sitemap)
│   └── static/
│       ├── css/
│       │   └── analytics.css     # CSS for analytics app
│       └── js/
│           └── analytics.js      # JavaScript for analytics interactivity
│
├── admin_portal/                # Admin portal app
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py                # Models for user preferences, notifications
│   ├── views.py                 # Views for user and preference management
│   ├── urls.py                  # URL routing for admin portal
│   ├── templates/
│   │   └── admin_portal/
│   │       ├── user_management.html    # User management dashboard
│   │       ├── notification_logs.html  # Notifications and alerts
│   │       └── preferences.html        # User preferences page
│   └── static/
│       ├── css/
│       │   └── admin_portal.css  # CSS for admin portal
│       └── js/
│           └── admin_portal.js   # JavaScript for admin portal interactivity
│
├── api_client/                  # Centralized API management app
│   ├── __init__.py
│   ├── services.py              # API service classes for DataForSEO, OpenAI, etc.
│   ├── utils.py                 # Helper functions for API interactions
│   └── ...
│
├── homepage/                    # Public homepage app
│   ├── __init__.py
│   ├── views.py                 # Views for public homepage
│   ├── urls.py                  # URL routing for homepage
│   ├── templates/
│   │   └── homepage/
│   │       └── index.html       # Public homepage template
│   └── static/
│       ├── css/
│       │   └── homepage.css     # CSS for homepage
│       └── js/
│           └── homepage.js      # JavaScript for homepage
```

### Development Order and Key Stages

#### 1. **Initial Setup**
   - Set up the Django project and configure the database (SQLite).
   - Create the core apps: `workitems`, `analytics`, `admin_portal`, `api_client`, and `homepage`.
   - Set up routing and base templates for each app.

#### 2. **WorkItems Management**
   - Build the `WorkItems` model and related task management.
   - Develop the Planner Page (kanban board) with drag-and-drop functionality.
   - Add views for creating and managing WorkItems and tasks.

#### 3. **Keyword Analytics Integration**
   - Build the `KeywordAnalytics` model for storing keyword data.
   - Implement the connection with the DataForSEO API via the `api_client` app.
   - Develop keyword analytics dashboards and link keyword data to WorkItems.

#### 4. **Personal Website Analytics**
   - Create the models for site traffic analytics (optional to start).
   - Build the visual sitemap for tracking page-specific performance.

#### 5. **Admin Portal**
   - Set up user management, roles, and permissions in the `admin_portal` app.
   - Add notification logging and user preferences (e.g., themes).

#### 6. **Interactive Sitemap and Personalization**
   - Create the interactive visual sitemap for site performance visualization.
   - Build functionality for tracking user preferences and personalizing their experience.

#### 7. **Final Adjustments and Optimization**
   - Review all app interactions, especially API calls and caching mechanisms.
   - Optimize for performance and ensure data is correctly stored and retrieved from SQLite.
   - Polish UI using Bootstrap and JavaScript for dynamic elements.

This roadmap will help you move forward step by step. Let me know if you need further clarification or adjustments!