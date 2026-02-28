# 🤝 New Client Onboarding — n8n Workflow

An automated workflow built with [n8n](https://n8n.io) that triggers whenever a new client is added to a Google Sheet. It sends a notification email to the owner, sends a thank-you email to the client, and saves the client to Google Contacts — all automatically, without processing the same client twice.

---

## 📋 What It Does

1. *Detects a new row* added to a Google Sheet
2. *Filters out already-processed rows* using a Processed column (prevents duplicate emails)
3. *Sends a notification email* to you (the owner) about the new client
4. *Creates a contact* in Google Contacts with the client's details
5. *Sends a thank-you email* to the new client
6. *Marks the row as processed* (Yes) in the Google Sheet so it's never triggered again

---

## 🔧 Workflow Structure


Google Sheets Trigger
        ↓
      If node (Processed ≠ Yes)
        ↓ true
  Send notification email (Gmail)
        ↓
  Create contact (Google Contacts)
        ↓
  Send thank-you email to client (Gmail)
        ↓
  Update row in Google Sheet (Processed = Yes)


---

## 🗂️ Google Sheet Structure

Your sheet must have the following columns:

| Column | Description |
|---|---|
| First Name | Client's first name |
| Last Name | Client's last name |
| Email | Client's email address |
| Phone number | Client's phone number |
| Description | Any notes or message from the client |
| Processed | Leave empty — workflow fills this with Yes after processing |

---

## ⚙️ Setup Instructions

### 1. Google Sheet
- Create a Google Sheet with the columns listed above
- Leave the Processed column empty for all rows

### 2. n8n Credentials
You will need to connect the following accounts in n8n:
- *Google Sheets* — for reading and updating the sheet
- *Gmail* — for sending emails (x2 nodes)
- *Google Contacts* — for saving new clients

### 3. Import the Workflow
- Download the workflow JSON file
- In n8n, go to *Workflows → Import*
- Upload the JSON file
- Update the credentials in each node

### 4. Configure the Nodes
- *Google Sheets Trigger:* point it to your sheet and set event to rowAdded
- *If node:* condition is Processed *is not equal to* Yes
- *Gmail nodes:* update the sender/recipient email addresses and email content
- *Google Contacts:* make sure fields are mapped correctly (phone number must be passed as a string using .toString())
- *Update row node:* set Column to match on to Email

---

## 🐛 Known Issues & Fixes

*Phone number type error*
Google Contacts API expects phone numbers as strings. If your sheet stores them as numbers, use this expression:

{{ $('Google Sheets Trigger').item.json['Phone number'].toString() }}


*Old rows being re-processed*
This is handled by the Processed column + If node. Make sure existing rows already have Yes in the Processed column before activating the workflow.

---

## 🛠️ Built With

- [n8n](https://n8n.io) — Workflow automation
- Google Sheets — Client data source
- Gmail — Email notifications
- Google Contacts — Contact management

---

## 📄 License

MIT — feel free to use and modify this workflow for your own projects.
