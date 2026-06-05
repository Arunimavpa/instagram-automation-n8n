# 📱 Instagram Automation — Sree Narayana Guru Quotes

An automated social media posting system built with **n8n** that daily posts Malayalam quotes of Sree Narayana Guru on Instagram with a beautiful image overlay — zero manual work required.

---

## 🎯 What It Does

- Reads quotes from Google Sheets automatically
- Generates a beautiful image with Malayalam text overlaid on a background image using hcti.io
- Posts the image to Instagram every day at a scheduled time
- Cross-posts to Facebook page automatically (via Instagram-Facebook link)
- Marks the quote as "Posted" in Google Sheets so it never repeats
- Sends a Telegram notification after every successful post

---

## ⚙️ Workflow

```
Schedule Trigger (daily)
    ↓
Google Sheets — read quotes
    ↓
Filter — skip already posted quotes
    ↓
Limit — pick 1 quote per day
    ↓
hcti.io API — generate image with Malayalam text
    ↓
Edit Fields — prepare image URL and quote
    ↓
Instagram Graph API — create media container
    ↓
Instagram Graph API — publish post
    ↓
Google Sheets — mark quote as "Posted"
    ↓
Telegram Bot — send notification
```

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation |
| [Google Sheets](https://sheets.google.com) | Quote database and status tracker |
| [hcti.io](https://hcti.io) | HTML to image generation with Malayalam font support |
| [Cloudinary](https://cloudinary.com) | Background image hosting |
| [Instagram Graph API](https://developers.facebook.com/docs/instagram-api) | Automated Instagram posting |
| [Telegram Bot API](https://core.telegram.org/bots) | Post notifications |

---

## 📋 Google Sheets Structure

| Column | Description |
|--------|-------------|
| `quote` | Malayalam quote text |
| `status` | Leave blank for unposted, system sets "Posted" after publishing |

---

## 🚀 Setup Instructions

### 1. Prerequisites
- n8n instance (self-hosted or cloud)
- Google Sheets account
- Instagram Business/Creator account
- Facebook Developer account with app
- hcti.io account (free)
- Cloudinary account (free)
- Telegram bot (optional)

### 2. Google Sheets
- Create a Google Sheet with columns: `quote`, `status`
- Add your quotes in the `quote` column
- Leave `status` column blank for unposted quotes

### 3. hcti.io
- Sign up at [hcti.io](https://hcti.io)
- Get your User ID and API Key from dashboard
- Add as Basic Auth credential in n8n

### 4. Instagram Graph API
- Create a Facebook Developer App
- Get your Instagram Account ID
- Generate a long-lived access token
- Add as Facebook Graph API credential in n8n

### 5. Import Workflow
- Download `insta_auto.json`
- In n8n go to **Import from file**
- Select the JSON file
- Update all credentials with your own
- Replace all `YOUR_*` placeholder values
- Set your desired schedule time
- Toggle **Active** to ON

---

## 📝 Credentials to Configure

After importing the workflow, replace these placeholders:

| Placeholder | Description |
|-------------|-------------|
| `YOUR_GOOGLE_SHEET_ID` | Your Google Sheet ID from the URL |
| `YOUR_INSTAGRAM_ACCOUNT_ID` | Your Instagram Business Account ID |
| `YOUR_CLOUDINARY_BACKGROUND_IMAGE_URL` | Your Cloudinary image URL |
| `YOUR_TELEGRAM_CHAT_ID` | Your Telegram chat ID |

---

## 💰 Cost

**Completely free!** All tools used have free tiers sufficient for daily posting:
- n8n — free (self-hosted)
- hcti.io — 100 free images/month
- Cloudinary — 25GB free storage
- Google Sheets — free
- Telegram — free

---

## 📸 Demo

> Workflow posts daily Malayalam quotes of Sree Narayana Guru to Instagram automatically.

Check out the live page: [@dev_daily_diva](https://www.instagram.com/dev_daily_diva) on Instagram

---

## 🙏 Inspiration

This project was built to spread the timeless teachings of **Sree Narayana Guru** — one of the greatest social reformers of Kerala — to a wider audience through daily automated social media posts.

> *"One Caste, One Religion, One God for Man"* — Sree Narayana Guru

---

## 📄 License

MIT License — feel free to use and modify for your own projects!
