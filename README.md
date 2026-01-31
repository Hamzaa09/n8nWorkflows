# 🎬 AI YouTube Video Generator | n8n Workflow

This n8n workflow automatically generates AI videos, uploads them to YouTube, stores records in Google Sheets, and sends notifications via WhatsApp and Email. All with just one command.

It is designed to demonstrate how AI & automation can remove repetitive content publishing tasks.

Demonstration Video: https://www.linkedin.com/feed/update/urn:li:activity:7423207127411884032/


# 🚀 Features

* 🤖 AI video generation via HeyGen API (HTTP request)
* 📤 Automatic YouTube upload
* 📊 Store video data in Google Sheets
* 💬 WhatsApp notification after upload
* 📧 Email notification after upload
* 🔄 Fully automated pipeline



# 🧩 Requirements

Before using this workflow, you need:

* n8n instance (cloud or self-hosted)
* Google account
* YouTube channel
* HeyGen API key
* WhatsApp API (Meta Business Suite)
* Gmail or SMTP email account



# ⚙️ Setup Guide

## 1️⃣ Import the Workflow

1. Download the workflow JSON file from this repo
2. Open n8n
3. Go to *Workflows*
4. Click *Import from File*
5. Select the JSON file
6. Save workflow



# 🔑 Credentials Setup

## 🔹 Google Credentials (YouTube + Sheets)

Used for:

* YouTube upload node
* Google Sheets node

### Steps:

1. Go to *Google Cloud Console*
2. Create a new project
3. Enable APIs:

   * YouTube Data API v3
   * Google Sheets API
4. Go to *Credentials → Create Credentials*
5. Create *OAuth Client ID*
6. Add redirect URL from n8n:

   
   https://YOUR-N8N-DOMAIN
   
7. Copy:

   * Client ID
   * Client Secret

### In n8n:

1. Go to *Credentials*
2. Create new credential:

   * Google OAuth2
3. Paste Client ID & Secret
4. Click *Connect*
5. Approve access

✅ Use this credential in:

* YouTube Node
* Google Sheets Node



## 🎬 HeyGen API (HTTP Request Node)

Used for:

* AI video generation

### Steps:

1. Create account at HeyGen
2. Get your API Key
3. Open your *HTTP Request* node in n8n

### Configure:

* Method: POST (or as used in your flow)
* URL: HeyGen endpoint
* Headers:


Authorization: Bearer YOUR_HEYGEN_API_KEY
Content-Type: application/json


* Body: JSON (already defined in workflow - update prompt/template if needed)

✅ No separate credential needed - header auth is enough.



## 💬 WhatsApp Credentials

Depends on which service you used.



### WhatsApp (Meta Business Suite)

Watch this video: https://www.youtube.com/watch?v=yPgkmNFOTtc&list=PL0PCSAR_cA6O6a3li7kZqyXpovuimnIeB&index=13



## 📧 Email Credentials

If using Gmail:

1. Create *Gmail OAuth2 credential* in n8n
2. Connect your account
3. Select it in Email node

If using SMTP:

Provide:

* Host
* Port
* Username
* Password



# ▶️ How to Run

1. Update all credentials
2. Open first trigger node
3. Provide prompt / input data
4. Click *Execute Workflow*
5. Flow will:


Prompt → AI Video → Process → YouTube Upload → Sheet Entry → Notifications




# 🧪 Testing Tips

* Test each node individually first
* Run HeyGen node alone to confirm video generation
* Test YouTube node with small sample file
* Use your own phone/email for notification test
* Add error node for failure handling (recommended)



# 💡 Notes

* This workflow uses free/limited AI tools for demo purposes
* You can replace video provider with any API
* Add delay nodes if API rate limits apply
* Can be extended with:

  * Title generator
  * Thumbnail AI
  * Auto description writer



# 🛠 Built With

* n8n
* HeyGen API
* YouTube API
* Google Sheets API
* WhatsApp API
