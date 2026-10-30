# CRM Practice Simulator

A single-file, browser-based CRM I use to practice virtual assistant work: managing contacts, moving deals through a pipeline, handling conversations, booking appointments, and building simple automations.

Everything in it is fictional. The contacts, companies, emails, phone numbers and messages are made-up sample data, and no real messages are sent.

## What's inside

- **Dashboard**: a summary of contacts, deals and activity
- **Contacts**: search, tags, notes and custom fields
- **Opportunities**: a drag-and-drop sales pipeline board
- **Conversations**: a simulated inbox for text and email threads
- **Calendars**: month, week and agenda views for appointments
- **Automation**: a visual workflow builder (triggers such as "Contact created" or "Opportunity stage changed", and actions such as send email, add tag, wait, create task)

## Run it

Open `index.html` in any modern browser. There is nothing to install and no build step.

The sign-in page is simulated and shows its own demo account. Your changes are saved in your browser's local storage only, so nothing leaves your computer.

## Why I built it

I use it to practice realistic client tasks. Next, I'm connecting it to [n8n](https://n8n.io) so that actions in the CRM, such as adding a contact, can trigger real automations like a welcome email or a log entry in Google Sheets.

## Notes

- Fonts load from Google Fonts. Without a connection, the browser falls back to system fonts.
- Built with plain HTML, CSS and JavaScript. No frameworks and no external services.
