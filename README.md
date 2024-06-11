

## Step-by-Step Procedure and Milestones

### Milestone 1: Setting Up the Project
1. **Initialize the Project**
   - Set up a Git repository for version control.
   - Initialize the React project with `create-react-app hackathon-platform`.
   - Install necessary dependencies:
     ```bash
     npm install @supabase/supabase-js @material-ui/core @material-ui/icons
     ```

2. **Create the Frontend (React)**
   - Set up the basic structure for your React application.
   - Organize folders for components, pages, and services.

3. **Set Up Supabase**
   - Create a Supabase project.
   - Set up authentication and database.
   - Integrate Supabase with your React frontend.

### Milestone 2: User Registration and Authentication
1. **User Registration and Login**
   - Create registration and login forms in React.
   - Use Supabase Auth for handling user authentication.
   - Implement email confirmation using Supabase's built-in email verification.

2. **Email Verification**
   - Use Supabase's email verification feature.
   - Customize email templates for registration confirmation and verification via Supabase dashboard.

### Milestone 3: Team Registration and Management
1. **Team Registration**
   - Create forms for team creation and joining existing teams.
   - Store team information and member associations in Supabase.

2. **Team Selection**
   - Implement functionality for team leaders to invite members via email.
   - Set up a process for approving team join requests.

### Milestone 4: Hackathon Rounds Management
1. **Database Schema Design**
   - Create tables in Supabase for users, teams, hackathon rounds, submissions, and judges.
   - Implement relationships between these tables.

2. **Schema Example**
   ```sql
   -- Users table
   CREATE TABLE users (
       id UUID PRIMARY KEY,
       email VARCHAR UNIQUE NOT NULL,
       password VARCHAR NOT NULL,
       name VARCHAR NOT NULL,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   -- Teams table
   CREATE TABLE teams (
       id UUID PRIMARY KEY,
       name VARCHAR NOT NULL,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   -- UserTeams table (many-to-many relation)
   CREATE TABLE user_teams (
       user_id UUID REFERENCES users(id),
       team_id UUID REFERENCES teams(id),
       PRIMARY KEY (user_id, team_id)
   );

   -- HackathonRounds table
   CREATE TABLE hackathon_rounds (
       id UUID PRIMARY KEY,
       round_number INT NOT NULL,
       description TEXT NOT NULL,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   -- Submissions table
   CREATE TABLE submissions (
       id UUID PRIMARY KEY,
       team_id UUID REFERENCES teams(id),
       round_id UUID REFERENCES hackathon_rounds(id),
       submission_link VARCHAR NOT NULL,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   -- Judges table
   CREATE TABLE judges (
       id UUID PRIMARY KEY,
       name VARCHAR NOT NULL,
       email VARCHAR UNIQUE NOT NULL,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

### Milestone 5: Submission Management
1. **Round 1: Video Submission**
   - Create a form for video submissions in React.
   - Integrate AWS S3 for video uploads. Use Supabase to store video links.
   - Use Supabase storage for video uploads if preferred.

2. **Round 2: Prototype Submission**
   - Create a form for prototype submissions.
   - Implement file upload handling and store links in Supabase.

3. **Round 3 and Final Round**
   - Manage team progress and store relevant data in Supabase.
   - Handle notifications for selected teams using Supabase functions.

### Milestone 6: Judge and Admin Panel
1. **Admin Panel**
   - Create an admin panel in React for managing hackathon rounds and submissions.
   - Implement functionality for screening and selecting teams.

2. **Judge Panel**
   - Create a panel for judges to review submissions.
   - Implement scoring and feedback mechanisms.

### Milestone 7: Final Polishing and Deployment
1. **Frontend Design and Usability**
   - Use design libraries like Material-UI for better UI components.
   - Implement responsive design for mobile compatibility.

2. **Testing**
   - Write unit and integration tests for your application.
   - Perform user testing to gather feedback and make necessary improvements.

3. **Deployment**
   - Deploy your frontend on Vercel or Netlify.
   - Ensure your Supabase instance is properly configured and secured.
   - Set up AWS S3 or Supabase storage for file uploads.
