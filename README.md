# CRM Practice Simulator

A single-file, browser-based CRM I use to practice virtual assistant work: managing contacts, moving deals through a pipeline, handling conversations, booking appointments, and building simple automations. It can also send its events to **n8n** to trigger real automations.

**Live demo:** [edmondpva.github.io/CRM-practice-simulator](https://edmondpva.github.io/CRM-practice-simulator/) · **Case study:** [my portfolio](https://edmondpva.github.io/portfolio)

![CRM dashboard](https://raw.githubusercontent.com/edmondPVA/portfolio/main/assets/crm-simulator/dashboard.jpg)

Everything in it is fictional. The contacts, companies, emails, phone numbers and messages are made-up sample data for a fictional remodeling company, and no real SMS, emails or calls are sent from the CRM itself.

## What's inside

- **Dashboard**: a summary of contacts, deals and activity
- **Contacts**: search, tags, notes and custom fields
- **Opportunities**: a drag-and-drop sales pipeline board
- **Conversations**: a simulated inbox for text and email threads
- **Calendars**: month, week and agenda views for appointments
- **Automation**: a visual workflow builder (triggers such as "Contact created" or "Opportunity stage changed", and actions such as send email, add tag, wait, create task)
- **n8n webhook**: sends CRM events to a real n8n workflow (see below)

## Run it

Open the [live demo](https://edmondpva.github.io/CRM-practice-simulator/) in any modern browser. There is nothing to install.

The sign-in page is simulated and shows its own demo account. Your changes are saved in your browser's local storage only, so each visitor gets their own copy of the sample data. Use **Reset sample data** in the account menu to start over.

## Connect it to n8n

The simulator can send each CRM event to an n8n workflow, so actions in the CRM trigger real automations, such as a welcome email or a new row in Google Sheets.

1. In n8n, create a workflow that starts with a **Webhook** node (method: POST) and copy its URL.
2. In the simulator, open the **account menu → n8n webhook**, paste the URL and click **Save**. The menu then shows **(on)**.
3. Use the CRM as normal. A toast confirms each event that reaches n8n.

**Events sent:**

| Event | When it fires |
| --- | --- |
| `contact_created` | A new contact is added |
| `tag_added` | A tag is added to a contact |
| `opp_stage` | A deal moves to a different pipeline stage |
| `appt_booked` | An appointment is booked |
| `customer_replied` | A customer replies in a conversation |

Each event is sent as JSON:

```json
{
  "event": "contact_created",
  "sentAt": "2026-11-26T03:00:00.000Z",
  "contact": { "firstName": "...", "lastName": "...", "email": "...", "phone": "...", "company": "...", "source": "...", "tags": [] },
  "details": { }
}
```

The webhook URL is saved only in your browser and is empty by default. Clear it to turn the connection off.

## Why I built it

I use it to practice realistic client tasks, and to show how a CRM can hand off work to automation tools. My n8n workflows for it send welcome, thank-you and feedback emails and log events to Google Sheets. The full write-up is on my [portfolio](https://edmondpva.github.io/portfolio).

## Notes

- Fonts load from Google Fonts. Without a connection, the browser falls back to system fonts.
- Built with plain HTML, CSS and JavaScript. No frameworks. The only outside connection is the optional n8n webhook.
