# Auto Ticket Classification using Flow Designer

## 📌 Project Overview

**Auto Ticket Classification using Flow Designer** is a ServiceNow-based IT helpdesk automation project developed to reduce the manual effort involved in classifying support tickets.

In a typical school IT helpdesk, users raise tickets for issues such as Wi-Fi problems, projector failures, password/login problems, and slow computers. Normally, an IT staff member has to read the ticket and manually decide the appropriate category and subcategory.

This project automates that classification process using **ServiceNow Flow Designer**.

When a new ticket is created, the workflow checks the issue description against predefined conditions and automatically assigns the appropriate **Category** and **Subcategory**. A confirmation email is also sent to the caller.

---

## 🎯 Objectives

The main objectives of this project are:

- Automatically classify IT support tickets.
- Reduce manual ticket classification.
- Maintain consistent Category and Subcategory values.
- Implement dependent Category/Subcategory choices.
- Automatically notify the caller after ticket creation.
- Store ticket information in a structured ServiceNow table.
- Provide a simple and maintainable no-code automation solution.

---

## 🛠️ Technology Used

| Component | Technology |
|---|---|
| Platform | ServiceNow |
| Automation | Flow Designer |
| Data Storage | ServiceNow Custom Table |
| Table | Incident WorkFlow |
| Notification | Flow Designer - Send Email |
| Configuration Management | Update Set |
| Classification | Predefined keyword/rule-based conditions |

> The current implementation does not use a separate Node.js backend, MongoDB database, external API or machine-learning model.

---

## 🏗️ System Architecture

The project is implemented completely within the ServiceNow platform.

```text
                    ┌──────────────────────┐
                    │   Student / Teacher  │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   ServiceNow Ticket  │
                    │        Form          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Incident WorkFlow   │
                    │    Custom Table      │
                    └──────────┬───────────┘
                               │
                        Record Created
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Flow Designer     │
                    │  Classification Flow │
                    └──────────┬───────────┘
                               │
                 ┌─────────────┼─────────────┐
                 │             │             │
                 ▼             ▼             ▼
             Wi-Fi        Projector      Password
                 │             │             │
                 ▼             ▼             ▼
             Network       Hardware       Access
                 │             │             │
                 └─────────────┼─────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Update Record     │
                    │ Category/Subcategory │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Send Email       │
                    │  Caller Notification │
                    └──────────────────────┘
