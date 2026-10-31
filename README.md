<div align="center">

![SmileCare AI Receptionist](assets/social-preview.png)

# SmileCare AI Receptionist

**A voice agent that answers the clinic phone, checks real availability, and books, reschedules and cancels appointments.**

Retell AI · n8n · Google Calendar · Google Sheets

</div>

---

## Demo

[![Watch the demo](assets/social-preview.png)](YOUR_DEMO_VIDEO_URL)


## What it does

Alia, the AI receptionist for the fictional **SmileCare Dental Clinic**, can:

- Answer clinic questions (location, hours, pricing, insurance) from a knowledge base, and never guess outside it
- Check Google Calendar for a free slot and offer up to three nearby alternatives when one is taken
- Book new appointments after spelling back and confirming the caller's name and phone number
- Find, reschedule and cancel existing appointments, verifying name and phone before any change
- Hand over to a human on request or in an emergency
- Log every call (caller, phone, summary, appointment status) to a sheet

## How it works

![Architecture](assets/architecture.png)

Retell AI runs the conversation. Each tool call is an authenticated HTTPS `POST` to an n8n webhook, which reads and writes Google Calendar (the source of truth for time slots) and Google Sheets (bookings and call log). A staff dashboard can read the bookings sheet.

![Call flow](assets/call-flow.png)

| Placeholder | Where it appears |
|---|---|
| `YOUR_WEBHOOK_API_KEY` | Retell tool headers + the n8n Header Auth credential |
| `https://n8n.your-domain.com/webhook/YOUR_WEBHOOK_PATH_HERE` | Retell tool URLs |
| `YOUR_GOOGLE_CALENDAR_ID@group.calendar.google.com` | Calendar nodes in n8n |
| `YOUR_GOOGLE_SHEET_ID`, `YOUR_CALL_LOG_SHEET_GID` | Sheets nodes in n8n |
| `+920000000000` | Human-transfer number in the Retell agent |
