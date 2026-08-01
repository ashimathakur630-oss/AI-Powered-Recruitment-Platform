# AI-Powered Recruitment Platform

An AI-powered recruitment and hiring automation platform built using **n8n, Supabase, Google Workspace, Groq AI, and Gemini AI**.

The system automates major stages of the recruitment process, starting from candidate registration and resume collection to AI-based resume screening, HR approval, interview scheduling, and recruitment analytics.

---

## 📌 Project Overview

Recruitment teams often spend significant time manually collecting applications, reviewing resumes, communicating with candidates, scheduling interviews, and maintaining recruitment records.

This project provides an automated recruitment workflow that integrates multiple cloud services and AI models into a single modular platform.

The system uses **n8n as the central workflow automation engine** and connects it with:

- Google Forms
- Google Drive
- Google Sheets
- Gmail
- Google Calendar
- Supabase
- Groq AI
- Gemini AI

The platform contains **five independent but interconnected workflows**.

---

## 🎯 Objectives

The main objectives of this project are:

- Automate candidate registration.
- Collect and store candidate resumes.
- Automatically process and analyze resumes.
- Use AI to evaluate candidate qualifications.
- Generate an AI-based candidate score.
- Identify candidate strengths and weaknesses.
- Generate preliminary recruitment recommendations.
- Provide an HR approval stage.
- Automate interview scheduling.
- Send automated email notifications.
- Maintain centralized recruitment records.
- Maintain workflow and audit information.
- Generate recruitment analytics and reports.

---

# 🏗️ System Architecture

The platform follows a modular workflow-based architecture.

```text
                    ┌─────────────────────┐
                    │    Candidate        │
                    │    Application      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Google Forms     │
                    └──────────┬──────────┘
                               │
                               ▼
                 ┌───────────────────────────┐
                 │           n8n              │
                 │   Workflow Automation     │
                 └─────────────┬─────────────┘
                               │
          ┌────────────────────┼────────────────────┐
          │                    │                    │
          ▼                    ▼                    ▼
   Google Drive           AI Processing          Supabase
   Resume Storage       Groq AI / Gemini AI     Database
          │                    │                    │
          └────────────────────┼────────────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │     HR Approval     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Google Calendar     │
                    │ Interview Scheduling│
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Gmail Notification  │
                    └─────────────────────┘

A detailed architecture diagram is available in:

Images/System_Architecture.png

🔄 Five n8n Workflows
Workflow 1 – Candidate Registration & Resume Collection

This workflow handles the initial candidate application.

Main operations
Candidate submits the recruitment form.
n8n receives the new application.
Candidate information is validated.
Resume information is processed.
Resume is stored in Google Drive.
Candidate details are stored in the recruitment database.
Candidate receives an application acknowledgement.
Technologies
Google Forms
n8n
Google Drive
Supabase / Google Sheets
Gmail
Workflow 2 – Resume Parsing & AI Evaluation

This workflow performs automated resume processing and preliminary candidate evaluation.

Main operations
Retrieve the candidate resume.
Extract resume text.
Send resume information to an AI model.
Analyze candidate skills and experience.
Generate an AI score.
Identify strengths.
Identify weaknesses.
Generate a recommendation.
Update the candidate record.
AI-generated information

The workflow can generate fields such as:

Candidate Name
Email
Phone
Skills
Experience
Education
AI Score
Strengths
Weaknesses
Recommendation
AI Technologies
Groq AI
Gemini AI

The AI stage is used as decision support and does not replace final human recruitment decisions.

Workflow 3 – Candidate Shortlisting & HR Approval

This workflow introduces a human approval stage into the automated recruitment pipeline.

Main operations
Retrieve evaluated candidate information.
Check the candidate's AI score/status.
Identify candidates requiring HR review.
Send candidate information to HR.
Provide Approve/Reject actions.
Wait for HR's decision.
Update the candidate status.
Record the decision for traceability.
Human-in-the-loop approach

The system does not automatically make the final hiring decision.

Instead:

AI Evaluation
      ↓
Shortlisting
      ↓
HR Review
      ↓
Approve / Reject
      ↓
Next Recruitment Stage

This allows HR to retain control over important recruitment decisions.

📅 Workflow 4 – Interview Scheduling

This workflow automates interview scheduling for approved candidates.

Main operations
Retrieve eligible candidates.
Check candidate information.
Create a Google Calendar event.
Add candidate and position details.
Set interview date/time.
Send interview invitation through Gmail.
Store interview information in Supabase.
Create an audit record.
Example Calendar Information

The calendar event can contain:

Candidate: John Smith
Position: Data Analyst
AI Score: 85
Email: john.smith@example.com
Location: Online Interview

The workflow therefore eliminates the need for HR to manually create every interview event.

📊 Workflow 5 – Recruitment Analytics & Reporting

The fifth workflow is designed to support recruitment monitoring and reporting.

It can process recruitment information and generate useful statistics such as:

Total applications
Shortlisted candidates
Rejected candidates
Approved candidates
Interviews scheduled
Recruitment status

The workflow can be executed on a scheduled basis using an n8n schedule/cron trigger.

This provides HR with a centralized view of recruitment activity.

🗄️ Database Design

The project uses Supabase as the centralized database.

The database stores candidate information as well as interview and workflow activity.

Candidates Table

The candidate table contains recruitment information such as:

Field	Description
Candidate ID	Unique candidate identifier
Name	Candidate name
Email	Candidate email
Phone	Candidate contact number
Position	Applied position
Resume File ID	Reference to stored resume
AI Score	AI-generated screening score
Status	Recruitment status
Interview Date	Scheduled interview date
Strengths	Candidate strengths
Weaknesses	Candidate weaknesses
Recommendation	AI recommendation
HR Decision	HR approval/rejection
Approved By	HR decision maker
Approval Time	Time of HR decision

Additional project-specific fields are also maintained in the database.

Interviews Table

The interview workflow maintains interview-related records including:

ID
Candidate ID
Workflow Name
Action
Status
Details

This table provides a structured record of interview-related automation.

Audit Logging

The system also maintains workflow/audit information.

Audit records help track:

Workflow execution
Actions performed
Status
Candidate-related events
Interview scheduling
HR decisions
Process details

This improves traceability and debugging.

🤖 AI Integration

The project integrates generative AI into the recruitment process.

Groq AI

Groq AI is used for fast language-model processing and structured candidate evaluation.

Gemini AI

Gemini AI is also used for generative AI-based resume understanding and evaluation.

The AI processing stage converts unstructured resume information into structured recruitment information.

Example
Resume
   ↓
Text Extraction
   ↓
AI Processing
   ↓
Candidate Information
   ↓
Skills + Experience
   ↓
AI Score
   ↓
Strengths / Weaknesses
   ↓
Recommendation
🔧 Technologies Used
Technology	Purpose
n8n	Workflow automation
Supabase	Database and data management
Google Forms	Candidate registration
Google Drive	Resume storage
Google Sheets	Tabular recruitment data/support
Gmail	Automated communication
Google Calendar	Interview scheduling
Groq AI	AI-powered resume evaluation
Gemini AI	Generative AI processing
Webhooks	HR approval interaction
Cron/Schedule Trigger	Automated reporting
📂 Project Structure
AI-Powered-Recruitment-Platform/
│
├── Documentation/
│   └── AI_Powered_Recruitment_Hiring_Platform_Project_Report.docx
│
├── Images/
│   ├── System_Architecture.png
│   └── ER_Diagram.png
│
├── Workflows/
│   ├── Workflow1_Candidate_Registration.json
│   ├── Workflow2_AI_Resume_Screening.json
│   ├── Workflow3_HR_Approval.json
│   ├── Workflow4_Interview_Scheduling.json
│   └── Workflow5_Analytics.json
│
└── README.md
📐 Entity Relationship Diagram

The project database follows a relational structure connecting candidates with interview and audit information.

The ER diagram is available at:

Images/ER_Diagram.png

✨ Key Features
AI-powered resume screening
Automated candidate registration
Cloud resume storage
AI-based candidate scoring
Strength and weakness extraction
Recruitment recommendation generation
Human approval mechanism
Automated interview scheduling
Google Calendar integration
Automated Gmail communication
Centralized Supabase database
Audit and workflow logging
Scheduled recruitment analytics
Modular n8n workflow architecture
🔐 Security Considerations

The repository does not contain confidential credentials or API keys.

Credentials for:

Groq AI
Gemini AI
Supabase
Google services

should be configured through n8n credentials/environment settings.

API keys, passwords, OAuth tokens and Supabase secret keys should never be committed to the repository.

🧪 Testing

The workflows were tested using sample candidate applications and resumes.

Testing included:

Candidate form submission
Resume upload
Resume retrieval
Resume text extraction
AI evaluation
Candidate score generation
Database updates
HR approval/rejection
Interview event creation
Gmail notifications
Interview database records
Audit information

The individual n8n workflow nodes were executed and verified during development.

📈 Project Results

The completed system successfully demonstrates an automated recruitment pipeline in which:

Candidate Application
        ↓
Resume Collection
        ↓
AI Resume Screening
        ↓
Candidate Shortlisting
        ↓
HR Approval
        ↓
Interview Scheduling
        ↓
Email Notification
        ↓
Database & Audit Records
        ↓
Recruitment Analytics

The project reduces repetitive recruitment activities and demonstrates the practical use of AI and workflow automation in Human Resources.

🚀 Future Scope

The platform can be further enhanced with:

Dedicated HR dashboard
Real-time recruitment analytics
Job description matching
Advanced skill-gap analysis
OCR for scanned resumes
Automated interview feedback processing
AI-generated interview questions
Interview performance analysis
Candidate ranking
Role-based access control
Advanced error handling and retry mechanisms
Additional communication channels
Enhanced recruitment reporting

📚 Documentation

The complete project report is available in the:

Documentation/

folder.

The exported n8n workflows are available in:

Workflows/

The system architecture and ER diagrams are available in:

Images/

👩‍💻 Author

Ashima Thakur

Project: AI-Powered Recruitment & Hiring Platform

Year: 2026

⭐ Project Summary

This project demonstrates how AI, workflow automation, cloud databases and Google Workspace services can be integrated to create an end-to-end recruitment automation platform.

The five-workflow architecture provides a modular, scalable and practical approach to automating candidate intake, AI-assisted screening, HR approval, interview scheduling and recruitment analytics.
