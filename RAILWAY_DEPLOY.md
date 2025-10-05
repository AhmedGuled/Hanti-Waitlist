# Railway Deployment Guide for Hanti Waitlist

## Prerequisites
1. Railway account (sign up at railway.app)
2. Git repository with your code
3. Email credentials (Gmail App Password recommended)

## Quick Deploy to Railway

### Method 1: Railway CLI (Recommended)

1. **Install Railway CLI:**
   ```bash
   npm install -g @railway/cli
   ```

2. **Login to Railway:**
   ```bash
   railway login
   ```

3. **Deploy from your project directory:**
   ```bash
   cd /Users/ahmedguled/Documents/Hanti-Waitlist-New
   railway deploy
   ```

### Method 2: GitHub Integration

1. **Push your code to GitHub:**
   ```bash
   git add .
   git commit -m "Prepare for Railway deployment"
   git push origin main
   ```

2. **Connect to Railway:**
   - Go to railway.app and log in
   - Click "New Project"
   - Select "Deploy from GitHub repo"
   - Choose your repository

## Environment Variables Setup

After deployment, add these environment variables in Railway dashboard:

```
PORT=3000
NODE_ENV=production
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-gmail-app-password
FROM_EMAIL=noreply@yourdomain.com
```

## Email Setup Guide

### Option 1: Gmail (Easiest for testing)
1. Enable 2FA on your Gmail account
2. Generate App Password:
   - Google Account → Security → 2-Step Verification → App passwords
   - Create password for "Mail"
3. Use your Gmail as SMTP_USER and app password as SMTP_PASS

### Option 2: SendGrid (Recommended for production)
1. Sign up at sendgrid.com
2. Create API key
3. Update environment variables:
   ```
   SMTP_HOST=smtp.sendgrid.net
   SMTP_PORT=587
   SMTP_USER=apikey
   SMTP_PASS=your-sendgrid-api-key
   ```

## Custom Domain Setup

1. In Railway dashboard, go to your project
2. Click "Settings" → "Domains"
3. Add your custom domain
4. Update your domain's DNS records as instructed

## Database

- SQLite database file (`waitlist.db`) will be created automatically
- For production, consider upgrading to PostgreSQL on Railway
- Railway provides free PostgreSQL databases

## Monitoring

- View logs in Railway dashboard
- Monitor performance and uptime
- Set up alerts for critical issues

## Local Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Start production server
npm start
```

Your app will be available at: `http://localhost:3000`

## Features Included

✅ Waitlist signup with email validation
✅ Automatic welcome emails
✅ Admin dashboard at `/admin`
✅ Rate limiting and security headers
✅ Mobile-responsive design
✅ SQLite database with auto-creation
✅ Launch notification system

## Support

For issues:
- Check Railway logs in dashboard
- Verify environment variables are set
- Test email configuration
- Ensure domain DNS is configured correctly