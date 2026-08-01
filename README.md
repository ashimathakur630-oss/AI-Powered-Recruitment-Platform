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
