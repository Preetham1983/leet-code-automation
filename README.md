LeetCode Consistency Bot 🤖

A personal automation script designed to keep your LeetCode grind consistent!
This bot checks your daily LeetCode progress and sends you email reminders every two hours until you've successfully completed at least one problem for the day.

Stay on track and crush your coding interview preparation! 🚀

✨ Features

📧 Automated Email Reminders: Sends reminder emails at a set interval to keep you accountable.

✅ Smart Submission Checking: Uses the LeetCode GraphQL API to check if you’ve made any successful submissions on the current day.

⏰ Customizable Schedule: The script is configured to start at 5:30 AM and run every 2 hours, but can be easily adjusted via a scheduler trigger in n8n automation or OS cron jobs.

🔑 Secure API Integration: Authenticates with the LeetCode API using your leetcode_session and csrftoken for secure data access.

⚙️ Easy Configuration: All sensitive keys, tokens, and email details are managed via environment variables for security and ease of setup.

🛠️ Tech Stack

Language: Python 🐍

API: LeetCode GraphQL API 🕸️

Networking: requests library

Scheduling: Cron Job ⏲️ (or any OS-level task scheduler)

Emailing: SMTP (smtplib) 📨

🚀 Getting Started

Follow these steps to get the automation up and running on your local machine or server.

✅ Prerequisites

Python 3.6+

A LeetCode account

A Gmail account (or other email provider) to send reminders

Important for Gmail: You need to generate an App Password instead of using your regular password. Follow Google’s instructions here
.

1. Clone the Repository
git clone https://github.com/your-username/leet-code-automation.git
cd leet-code-automation

2. Install Dependencies

It’s recommended to use a virtual environment.

# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# Install required packages
pip install -r requirements.txt


Note: You need to create a requirements.txt file with libraries like:

requests
python-dotenv

3. Configuration

This project uses environment variables to handle your secrets securely.

Create a file named .env in the project root.

Copy contents from .env.example into your new .env.

.env.example
# LeetCode API Credentials
LEETCODE_SESSION="YOUR_LEETCODE_SESSION_COOKIE"
CSRF_TOKEN="YOUR_CSRF_TOKEN"

# Email Configuration
SENDER_EMAIL="your_email@gmail.com"
SENDER_PASSWORD="YOUR_GMAIL_APP_PASSWORD"   # Not your regular password!
RECEIVER_EMAIL="your_personal_email@example.com"

🔑 How to Get LEETCODE_SESSION and CSRF_TOKEN

Log in to your LeetCode account in your browser.

Open Developer Tools (F12 or Ctrl+Shift+I).

Go to the Network tab.

Refresh the page or open any problem.

Look for a request made to:

https://leetcode.com/graphql


Click the request → check Request Headers.

Find the cookie header → inside it, you’ll see:

LEETCODE_SESSION=...;
csrftoken=...;


Copy those values and paste them into your .env file.

⏰ Scheduling

By default, the script is set to run at 5:30 AM and repeat every 2 hours.

On Linux/Mac, use a cron job:

crontab -e


Then add:

30 5-23/2 * * * /usr/bin/python3 /path/to/leet-code-automation/main.py


On Windows, use Task Scheduler or integrate with n8n automation.

📧 Email Notifications

The bot uses SMTP to send reminder emails.

Make sure less secure apps is disabled (if using Gmail, use App Passwords).

You will receive emails like:

✅ "Great job! You’ve solved a problem today 🎉"

⏰ "Reminder: No submissions yet today, keep grinding 💪"

🎯 Why Use This?

Keeps your consistency streak alive 🔥

Builds the habit of daily problem-solving

Holds you accountable with gentle nudges via email

Saves you from the "oops, I forgot to code today" moments 😅

📌 Future Improvements

Telegram/Slack notifications instead of only email

Smarter analytics on your daily submissions

Web dashboard to track streaks
