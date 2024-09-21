## Sebdue
## Video Demo: https://studio.youtube.com/video/MbZRLFVhqp0/edit
## Description:
# Project Structure and Functionality Description

Web application for managing and sending WhatsApp message campaigns. 
It consists of both a frontend built with React and a backend built with FastAPI. 
* the db and server connection is done using AWS services
The application allows users to create business profiles, manage contacts, create posts, and send campaigns. 
Here's a detailed breakdown of the project structure and functionality:

## Frontend (React)

The frontend is built using React and is structured into several key components:

### 1. Landing Page
- `Landing_page.js`

### 2. Authentication and User Management

- `login.js`: Handles user authentication, using Google OAuth.
- `AuthContext.js`: Provides authentication context throughout the app.

### 3. Dashboard and Main Application

- `Dashboard.js`: The main dashboard .
- `Campaign.js`: Manages campaign creation and viewing.
- `Leads.js`: Handles lead management.
- `Business.js`: Manages business profiles.
- `Posts.js`: Handles post creation and management.

### 4. Campaign Creation Flow

- `steps_leads.js`: Step for selecting leads for a campaign.
- `steps_business.js`: Step for selecting or creating a business profile.
- `steps_post.js`: Step for creating or selecting a post.
- `steps_deploy.js`: Final step for deploying a campaign.

### 5. Utility Components

- `CustomTable.js`: A reusable table component.
- `ImportWindow.js`: Handles file imports for leads and media.
- `DatePicker.js`: A custom date picker component.
- `ActionButton.js`, `DeleteButton.js`: Reusable button components.

### 6. Styling and Layout

- The project uses a combination of styled-components and inline styles for styling.
- `Layout.js` and `Steps_layout.js`: Provide consistent layouts for different parts of the application.

### 7. API Integration

- `campaignAPI.js`: A centralized file for API calls to the backend.

=======================================================================================
=======================================================================================

## Backend (FastAPI)

The backend is built with FastAPI and uses SQLAlchemy for database operations. 
It's structured as follows:

### 1. Main Application

- `main.py`: The entry point of the application, setting up FastAPI and database connections.

### 2. API Routes

- `routes.py`: Defines all API endpoints for authentication, leads, businesses, posts, and campaigns.

### 3. Authentication

- `auth.py`: Handles user authentication, likely using Google OAuth.

### 4. Database Models

- Various model files (`user_model.py`, `business_model.py`, `campaign_model.py`, etc.): Define database schemas.

### 5. Business Logic

- `campaign.py`: Handles campaign creation and management.
- `leads.py`: Manages lead processing and storage.
- `post.py`: Handles post creation and management.
- `business.py`: Manages business profile creation and retrieval.

### 6. Configuration

- `config.py`: Stores configuration settings.
- `database.py`: Sets up database connection.


=======================================================================================
=======================================================================================


## Functionality Overview

1. **User Authentication**: Users can sign up and log in using Google OAuth. The frontend stores the authentication token and includes it in API requests.

2. **Lead Management**: 
   - Users can import leads from spreadsheets or manually enter them.
   - The `ImportWindow` component handles file uploads.
   - Imported leads are processed and stored in the database.

3. **Business Profile Management**:
   - Users can create and manage multiple business profiles.
   - Profiles include details like name, description, location, and social media links.
   - Users can upload a profile picture for their business.

4. **Post Creation**:
   - Users can create posts with text, media (images or videos), and interactive buttons.
   - The post editor supports emoji insertion and previews the post in real-time.

5. **Campaign Creation**:
   - The campaign creation process is broken down into steps (leads, business, post, deploy).
   - Users select leads, choose a business profile, create or select a post, and set deployment options.
   - The `CampaignContext` maintains state across these steps.

6. **Campaign Deployment**:
   - Campaigns can be scheduled or sent immediately.
   - The backend handles the logic for sending messages to the selected leads.

7. **Dashboard and Analytics**:
   - Users can view their campaigns, leads, and business profiles.
   - The dashboard likely provides analytics on campaign performance.

8. **WhatsApp Integration**:
   - The backend integrates with the WhatsApp Business API to send messages.
   - It handles template approvals and message sending limits.

9. **File Handling**:
   - The application supports uploading and processing of spreadsheets for leads.
   - Images can be uploaded for business profiles and posts.

10. **Error Handling and Validation**:
    - Both frontend and backend implement error handling and input validation.
    - Error messages are displayed to users when operations fail.

11. **Responsive Design**:
    - The frontend uses responsive design techniques to ensure compatibility across devices.

12. **Security**:
    - Authentication tokens are used to secure API endpoints.
    - The backend likely implements rate limiting and other security measures.

13. **Database Operations**:
    - SQLAlchemy is used for database operations, providing an ORM layer.
    - Operations are abstracted into separate files (e.g., `campaign.py`, `leads.py`) for better organization.

14. **AWS Integration**:
    - The application uses AWS services like S3 for file storage and SQS for message queuing.

15. **Scalability Considerations**:
    - The use of message queues (SQS) suggests the application is designed to handle large volumes of messages.
    - The separation of concerns in the backend allows for potential microservices architecture in the future.

Thank you very much :) 