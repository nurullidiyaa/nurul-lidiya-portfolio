# EmailJS Setup Instructions

Follow these steps to configure EmailJS for your contact form:

## Step 1: Create an EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Sign up for a free account (free tier includes 200 emails/month)

## Step 2: Create an Email Service

1. Go to [Email Services](https://dashboard.emailjs.com/admin/integration)
2. Click "Add New Service"
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the setup instructions
5. **Copy your Service ID** (you'll need this)

## Step 3: Create an Email Template

1. Go to [Email Templates](https://dashboard.emailjs.com/admin/template)
2. Click "Create New Template"
3. Use this template structure:

```
Subject: {{subject}}

From: {{from_name}} ({{from_email}})

Message:
{{message}}

---
This email was sent from your portfolio contact form.
```

4. **Copy your Template ID** (you'll need this)

## Step 4: Get Your Public Key

1. Go to [Account > General](https://dashboard.emailjs.com/admin/account/general)
2. Find your **Public Key** (also called API Key)
3. **Copy your Public Key** (you'll need this)

## Step 5: Configure Environment Variables

1. Create a `.env.local` file in the root of your project
2. Add your credentials:

```env
VITE_EMAILJS_SERVICE_ID=your_service_id_here
VITE_EMAILJS_TEMPLATE_ID=your_template_id_here
VITE_EMAILJS_PUBLIC_KEY=your_public_key_here
```

3. Replace the placeholder values with your actual credentials
4. **Important:** The `.env.local` file is already in `.gitignore` and won't be committed to git

## Step 6: Test Your Setup

1. Start your development server: `npm run dev`
2. Go to the contact form
3. Fill out and submit the form
4. Check your email inbox for the message

## Troubleshooting

- **"EmailJS is not configured" error**: Make sure your `.env.local` file exists and has the correct variable names
- **Email not received**: Check your EmailJS dashboard for error logs
- **CORS errors**: Make sure your domain is added to EmailJS allowed origins (if needed)

## Security Note

Never commit your `.env.local` file to version control. It's already in `.gitignore` for safety.

