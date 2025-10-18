# n8n Automation Workflows

> Automated Business Intelligence & Workflow Systems

**Quick Stats:** 3 Workflows | 365+ Hours Saved Annually | ₹182,500+ Cost Savings

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Installation & Setup](#installation--setup)
3. [Workflow 1: Email Automation](#workflow-1-email-automation-system)
4. [Workflow 2: Sales Report with Charts](#workflow-2-sales-report-with-charts)
5. [Workflow 3: AI Analysis Report](#workflow-3-ai-powered-analysis-report)
6. [Telegram Auto-Reply System](#telegram-auto-reply-system)
7. [API Credentials Setup](#api-credentials-setup)
8. [Troubleshooting](#troubleshooting)

---

## Project Overview

| Project | Time Saved | Complexity | Status |
|---------|------------|------------|--------|
| Email Automation | 65 hrs/year | ⭐⭐ | ✅ Production |
| Sales Charts Report | 120 hrs/year | ⭐⭐⭐ | ✅ Production |
| Sales Analysis Report | 180 hrs/year | ⭐⭐⭐⭐ | ✅ Production |
| Telegram Auto-Reply | Custom | ⭐⭐⭐ | ✅ Production |

### Business Impact
```
Annual time saved: 365+ hours
Average hourly rate: ₹500
Annual cost savings: ₹182,500
Setup time investment: 15 hours
ROI: 2,333%
```

---

## Installation & Setup

### Prerequisites
- n8n account (cloud or self-hosted)
- Google Sheets API access
- Gmail account with OAuth2
- Telegram Bot Token
- API2PDF account (for report generation)

### Quick Start (5 minutes)

1. **Clone this repository**
```bash
git clone https://github.com/yourusername/n8n-automation-workflows.git
cd n8n-automation-workflows
```

2. **Import a workflow into n8n**
   - Open your n8n instance
   - Go to "Dashboard" → "Import"
   - Select JSON file from `workflows/` folder
   - Click "Import"

3. **Add credentials** (see [API Credentials Setup](#api-credentials-setup))
   - Google Sheets OAuth2
   - Gmail OAuth2
   - Telegram Bot API
   - API2PDF key

4. **Update configuration**
   - Replace `SHEET_ID` with your Google Sheet ID
   - Replace `CHAT_ID` with your Telegram Chat ID
   - Modify recipient emails

5. **Test manually**
   - Click "Test" in n8n
   - Verify output
   - Enable schedule if working

---

## Workflow 1: Email Automation System

### What It Does
Sends daily batch emails with 1-3 dynamic attachments from Google Sheets. Reduces manual work from 15 minutes to 2 minutes.


https://github.com/sowmiyad92-art/n8n-automation-portfolio/blob/main/Report%202.png

### Files
- `workflows/daily-bulk-sheet-email.json`

### How It Works
```
1. Daily scheduler triggers at 12:00 AM
2. Reads email config from Google Sheet
3. Downloads up to 3 template files
4. Merges email data with templates
5. Sends emails with attachments
6. Batches 10 emails at a time
```

### Features
- ✅ Multiple attachment support (1, 2, or 3 files)
- ✅ Google Sheets integration for recipients
- ✅ Dynamic subject lines and personalization
- ✅ CC/BCC support
- ✅ Batch processing to avoid rate limits
- ✅ Template variable substitution

### Setup Steps

**Step 1: Prepare Google Sheet**
Create a sheet with these columns:
```
RecipientEmail | Subject | MessageBody | CC | Template1 | Template2 | Template3
user@email.com | Welcome | Hi {Name} | - | [URL] | [URL] | -
```

Variables you can use in MessageBody:
- `{RecipientName}` - recipient's name
- `{Subject}` - email subject
- `{Day}` - current day (Monday, Tuesday, etc.)
- `{Date}` - current date (Jan 1, 2024)

**Step 2: Import workflow**
- Download: `daily-bulk-sheet-email.json`
- Import into n8n

**Step 3: Add credentials**
- Connect Google Sheets OAuth2
- Connect Gmail OAuth2

**Step 4: Update nodes**
In "Read Email Configuration" node:
- Document ID: Your Google Sheet ID
- Sheet: EmailConfig tab (or your sheet name)

**Step 5: Customize schedule**
In "Daily Schedule1" node:
- Change hour from `0` (midnight) to your preferred time

**Step 6: Test**
- Click "Test"
- Check Gmail account for test email

### Example Configuration
```
Sheet ID: 1s6q0x8DyweZqFO4wPIV0qkJgGy3jvWS18XTue0CwGKw
Email template URL: https://docs.google.com/document/d/abc123/export?format=pdf
Recipient: your-team@company.com
Schedule: Every day at 12:00 AM
```

### Troubleshooting
- **Email not sending**: Check Gmail OAuth2 credentials
- **Attachments missing**: Verify template URLs are accessible
- **Wrong recipients**: Update Google Sheet data
- See [Troubleshooting](#troubleshooting) section below

---

## Workflow 2: Sales Report with Charts

### What It Does
Generates professional sales reports with 3 dynamic charts (Line, Bar, Pie) and sends via Telegram. Fully automated weekly delivery.

https://github.com/sowmiyad92-art/n8n-automation-portfolio/blob/5a4404fa23f2726d3d60b5f2cea3c39733ae5bc5/Report%203.png


### Files
- `workflows/corrected-report-setup.json` (Chart version)

### How It Works
```
1. Weekly scheduler triggers
2. Fetches sales data from Google Sheets
3. Calculates totals and aggregates
4. Generates 3 charts using QuickChart.io
5. Creates HTML with embedded charts
6. Converts to PDF using API2PDF
7. Sends PDF via Telegram
```

### Features
- ✅ Line chart (sales trend over time)
- ✅ Bar chart (sales by product)
- ✅ Pie chart (regional distribution)
- ✅ Professional HTML layout
- ✅ Key metrics summary box
- ✅ Detailed transaction table
- ✅ Telegram bot delivery
- ✅ Auto-generated captions

### Setup Steps

**Step 1: Prepare Google Sheet**
Create a sheet named "SalesData" with columns:
```
Date | Month | Product | Sales | Quantity | Region | CustomerType
2024-01-01 | January | Product A | 5000 | 10 | North | Retail
2024-01-02 | January | Product B | 3500 | 8 | South | Wholesale
```

**Step 2: Import workflow**
- Download: `corrected-report-setup.json`
- Import into n8n

**Step 3: Add credentials**
- Google Sheets OAuth2
- API2PDF account (get free tier at api2pdf.com)
- Telegram Bot API

**Step 4: Update Sheet IDs**
In these nodes, replace with your Sheet ID:
- "Get row(s) in sheet3" → Document ID

**Step 5: Set Telegram Chat ID**
In "Send a document3" node:
- Chat ID: Your Telegram Chat ID (find with @userinfobot)

**Step 6: Test**
- Manually trigger workflow
- Check Telegram for PDF report

### Chart Details
| Chart | Data Source | Purpose |
|-------|-------------|---------|
| Line | Sales by Month | Track trends over time |
| Bar | Sales by Product | Compare product performance |
| Pie | Sales by Region | Show regional distribution |

### Example Output
```
Total Sales: ₹2,82,000
Total Quantity: 450 units
Average Sale: ₹5,600
Top Product: Product A (45% share)
Top Region: North (52% share)
Transactions: 50
```

### Customization
- **Change chart colors**: Edit the color arrays in HTTP chart nodes
- **Change report frequency**: Modify Schedule Trigger (cron expression)
- **Modify chart size**: Update width/height in URLs
- **Change layout**: Edit HTML/CSS in "Code in JavaScript3" node

---

## Workflow 3: AI-Powered Analysis Report

### What It Does
Advanced statistical analysis with executive summaries, Pareto analysis, anomaly detection, and strategic recommendations. Generates text-based professional analysis.

https://github.com/sowmiyad92-art/n8n-automation-portfolio/blob/b5d1cbed66695c3a8b8a412ca0da52a0e0aa3194/Report%204.png

### Files
- `workflows/corrected-report-setup.json` (Analysis version - Schedule Trigger1)

### How It Works
```
1. Weekly scheduler triggers
2. Fetches sales data from Google Sheets
3. Auto-detects data structure
4. Calculates statistical metrics:
   - Pareto analysis (80/20 rule)
   - Anomaly detection (Z-score method)
   - Trend analysis
   - Performance segmentation
5. Generates insights and recommendations
6. Creates professional HTML report
7. Converts to PDF via API2PDF
8. Sends to Telegram
```

### Advanced Analytics
- **Pareto Analysis**: Identifies which products drive 80% of sales
- **Anomaly Detection**: Finds unusual spikes or drops using Z-score (2-sigma threshold)
- **Trend Analysis**: Detects if performance is increasing/decreasing/accelerating
- **Performance Segmentation**: Categorizes into High/Medium/Low performers
- **Concentration Risk**: Calculates market share concentration
- **Regional Balance**: Uses coefficient of variation for balance assessment

### Features
- ✅ Executive summary (auto-generated)
- ✅ Key insights (4-5 bullets)
- ✅ Top performer analysis
- ✅ Areas needing attention
- ✅ 5+ strategic recommendations
- ✅ Growth rate calculations
- ✅ Multi-page professional layout
- ✅ Detailed transaction table

### Setup Steps

**Step 1: Prepare Google Sheet**
Same as Charts workflow:
```
Date | Month | Product | Sales | Quantity | Region | CustomerType
```

**Step 2: Import workflow**
- Download: `corrected-report-setup.json`
- Import into n8n
- Use "Schedule Trigger1" path (not Schedule Trigger3)

**Step 3: Add credentials**
- Google Sheets OAuth2
- API2PDF account
- Telegram Bot API

**Step 4: Update configuration**
- Sheet ID in "Get row(s) in sheet1"
- Chat ID in "Send a document1"

**Step 5: Test**
- Run manually
- Check Telegram for PDF

### Sample Analysis Output
```
Executive Summary:
"Performance analysis of 50 transactions reveals increasing 
trend with 22.5% growth. Total sales of ₹2,82,000 generated 
with ₹5,640 average transaction value..."

Key Insights:
- Positive momentum: increasing by 22.5%
- Product A leads with 45% market share
- North region dominates with 52% distribution
- No significant anomalies detected
- Top 3 products contribute 78% of sales

Recommendations:
1. Allocate 60% resources to top 3 products (₹1,70,000 focus)
2. Investigate underperformers for turnaround strategy
3. Scale North region operations (proven success)
4. Maintain current growth momentum
5. Monitor for trend changes weekly
```

### Customization
- **Analysis depth**: Add more statistical methods in "Generate Smart Analysis" node
- **Report length**: Adjust recommendations count
- **Metrics**: Add/remove metrics in analytics section
- **Thresholds**: Change Z-score threshold (currently 2-sigma)

---

## Telegram Auto-Reply System

### What It Does
Captures Telegram messages 24/7, extracts URLs from social platforms, saves to Google Sheets, and allows batch replies with one click.

### Files
- `workflows/autoreply.json`

### How It Works
```
1. Telegram message received
2. Extract message text and metadata
3. Parse URLs from:
   - Instagram (posts, reels, TV)
   - LinkedIn (posts, feed updates)
   - Twitter/X (status URLs)
   - Facebook (posts, videos, shares)
   - Deal sites (c21media.net links)
4. Remove URLs from description text
5. Save to Google Sheets with:
   - Message content
   - Extracted URLs
   - Sender info
   - Timestamp
6. Mark status as "Pending"
7. You add replies in Google Sheet
8. Manual trigger sends all pending replies
9. Status updates to "Sent"
```

### Features
- ✅ 24/7 message listening
- ✅ Multi-platform URL extraction
- ✅ Automatic message logging
- ✅ Metadata capture (Chat ID, User ID, Timestamp)
- ✅ Bulk reply capability
- ✅ Reply status tracking
- ✅ Threaded replies (replies to original messages)

### Setup Steps

**Step 1: Create Telegram Bot**
1. Message @BotFather on Telegram
2. Send `/newbot`
3. Enter bot name and username
4. Copy the API token

**Step 2: Prepare Google Sheet**
Create columns:
```
Message | Sender Name | Chat ID | Message ID | Timestamp | Status | Extracted URL | Reply | Reply Status
```

**Step 3: Import workflow**
- Download: `autoreply.json`
- Import into n8n

**Step 4: Add credentials**
- Telegram Bot API: Paste token from step 1
- Google Sheets OAuth2

**Step 5: Update configuration**
- In "Telegram Trigger" node: Verify webhook is created
- In "Append row in sheet" node: Update Sheet ID
- In "Get row(s) in sheet" node: Update Sheet ID
- Replace Chat IDs with your actual Telegram Chat ID

**Step 6: Test**
- Send message to your bot
- Check Google Sheet for logged message
- Add reply in sheet
- Click "Execute workflow" in n8n

### URL Extraction Examples
Supported formats:
```
Instagram: https://instagram.com/p/ABC123/ → Extracted
LinkedIn: https://linkedin.com/posts/ABC123 → Extracted
Twitter: https://x.com/user/status/123456 → Extracted
Facebook: https://facebook.com/share/ABC123 → Extracted
Deal site: https://c21media.net/property/123 → Extracted
```

### Workflow
```
Message received → URL extracted → Sheet logged (Pending)
    ↓
You read in Sheet
    ↓
Type reply in "Reply" column
    ↓
Click "Execute workflow" button
    ↓
All pending replies sent threaded to original
    ↓
Status updates to "Sent" automatically
```

### Customization
- **Add more platforms**: Update regex patterns in JavaScript code node
- **Auto-reply instead of manual**: Remove the Sheet read step
- **Filter messages**: Add conditional logic before logging

---

## API Credentials Setup

### Google Sheets OAuth2

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create new project
3. Enable APIs:
   - Google Sheets API
   - Google Drive API
4. Create OAuth 2.0 credentials (Desktop app)
5. Download JSON credentials
6. In n8n:
   - Click "Create new" → "Google Sheets"
   - Select "Service Account" or "OAuth2"
   - Paste credentials JSON

### Gmail OAuth2

1. Same Google Cloud project as above
2. Enable "Gmail API"
3. Create OAuth 2.0 credentials
4. In n8n:
   - Create new Gmail credential
   - Click "Connect my account"
   - Authorize n8n to access Gmail

### Telegram Bot API

1. Open Telegram, find @BotFather
2. Send `/newbot`
3. Enter bot name and username
4. Copy token (looks like: `123456789:ABCdefGHIjklmnoPQRstuvWXYZ`)
5. In n8n:
   - Create new Telegram credential
   - Paste token

**Find your Telegram Chat ID:**
- Message @userinfobot
- It replies with your Chat ID
- Use this in workflow nodes

### API2PDF

1. Go to [api2pdf.com](https://api2pdf.com)
2. Sign up (free tier available)
3. Get API key from dashboard
4. In n8n:
   - Create new credential for "HTTP Header Auth"
   - Header name: `Authorization`
   - Value: `Bearer YOUR_API_KEY`

### QuickChart.io

- No credentials needed (free public API)
- Charts generated automatically in workflow

---

## Repository Structure

```
---

## Troubleshooting

### General Issues

**"Credentials not found" error**
- Go to workflow node
- Click credential selector
- Create new credential or select existing
- Save node

**Workflow not triggering**
- Check Schedule Trigger node settings
- For Telegram: Verify webhook is active
- Manually test with "Execute workflow" button

**Missing Google Sheets data**
- Verify Sheet ID matches your sheet
- Check column names match node configuration
- Ensure you have read access to sheet

### Email Workflow

**Emails not sending**
- Verify Gmail OAuth2 is connected (green checkmark)
- Check recipient email addresses in Sheet
- Test with single recipient first
- Check Gmail spam folder

**Attachments not downloading**
- Verify template URLs are public (accessible without login)
- Check URLs are direct download links
- Test URL in browser manually

### Report Workflows

**PDF not generating**
- Verify API2PDF credentials are correct
- Check API2PDF account has quota remaining
- Ensure HTML is valid (check console for errors)
- Try generating with simpler data first

**Charts not showing**
- Verify data has values (not empty)
- Check chart labels are populated
- Try manual execution with test data

**Telegram not receiving file**
- Verify Chat ID is correct (@userinfobot)
- Check Telegram Bot has permission to send files
- Ensure PDF is under 50MB
- Verify Telegram credential is connected

### Telegram Auto-Reply

**Messages not logging to Sheet**
- Verify webhook is active in n8n
- Send test message to bot
- Check "Recent" tab in n8n shows execution
- Verify Google Sheets credential is connected

**Replies not sending**
- Ensure replies are typed in "Reply" column
- Click "Execute workflow" button
- Check Telegram status shows "Sent"
- Verify Chat ID matches sender's Chat ID

**URL extraction not working**
- Update regex patterns if format changes
- Test with known URL format
- Check JavaScript code for syntax errors

---

## Performance Metrics

### Execution Times
- Email workflow: ~10 seconds
- Charts report: ~15 seconds
- Analysis report: ~12 seconds
- Telegram reply: ~5 seconds per message

### Data Limits
- Max emails per batch: 50
- Max rows in report: 10,000
- Max attachment size: 25MB
- Max PDF size: 50MB

---

## Technical Skills Demonstrated

- Workflow automation and orchestration
- REST API integration and OAuth2 authentication
- JavaScript data processing and transformation
- Statistical analysis and anomaly detection
- HTML/CSS for report generation
- Pareto analysis and performance segmentation
- Webhook configuration
- Error handling and conditional logic

---

## License

MIT License - Feel free to use and modify for your own projects

---

## Support

For issues or questions:
1. Check [Troubleshooting](#troubleshooting) section
2. Review individual workflow setup steps
3. Check n8n documentation: https://docs.n8n.io

---

**Created with n8n | QuickChart.io | API2PDF | Google Workspace**
