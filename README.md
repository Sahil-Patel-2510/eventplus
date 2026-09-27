# Event Plus

A polished event-planning website with login, registration, enquiry forms, and local file-based storage. No database is required.

## Setup

1. Install dependencies:
   npm install

2. Start the server:
   npm start

3. Open the app:
   http://localhost:5000

All user and enquiry records are stored live inside the `db/` folder as JSON files:

- `db/eventplus.users.json`
- `db/eventplus.enquiries.json`

This means the data persists on disk without needing MongoDB, MySQL, or any external database service.

## OTP setup

Orders require OTP verification on the submitted email and mobile number. Add an SMTP account and either the provider API settings or Twilio settings to `.env` before using order confirmation:

   SMTP_HOST=smtp.example.com
   SMTP_PORT=587
   SMTP_SECURE=false
   SMTP_USER=your-smtp-user
   SMTP_PASSWORD=your-smtp-password
   SMTP_FROM=Event Plus <no-reply@example.com>
   OTP_API_URL=https://your-otp-provider.example/send
   OTP_API_KEY=your-server-side-api-key
   TWILIO_ACCOUNT_SID=your-account-sid
   TWILIO_AUTH_TOKEN=your-auth-token
   TWILIO_FROM=+10000000000

The OTP expires after 10 minutes. For local development only, the app also allows a fallback OTP flow unless `OTP_DEV_MODE=false`.

## API endpoints

- POST /api/register
- POST /api/login
- POST /api/enquiry
- POST /api/send-otp
- POST /api/verify-otp
- GET /api/health
