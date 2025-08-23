LeetCode Consistency Bot 🤖
A personal automation script designed to keep your LeetCode grind consistent! This bot checks your LeetCode progress and sends you email reminders every two hours until you've successfully completed a problem for the day.


Stay on track and crush your coding interview preparation! 🚀

✨ Features
📧 Automated Email Reminders: Sends reminder emails at a set interval to keep you accountable.

✅ Smart Submission Checking: Uses the LeetCode GraphQL API to check if you have made any successful submissions on the current day.

⏰ Customizable Schedule: The script is configured to start at 5:30 AM and run every 2 hours, but can be easily adjusted via a schedular trigger in n8n automation.

🔑 Secure API Integration: Authenticates with the LeetCode API using your personal leetcode_session and csrftoken for secure data access.

⚙️ Easy Configuration: All sensitive keys, tokens, and email details are managed via environment variables for security and ease of setup.

🛠️ Tech Stack
Language: Python 🐍

API: LeetCode GraphQL API 🕸️

Networking: HTTP Requests (requests library)

Scheduling: Cron Job ⏲️ (or any OS-level task scheduler)

Emailing: SMTP (smtplib) 📨

🚀 Getting Started
Follow these steps to get the automation up and running on your local machine or server.

Prerequisites
Python 3.6+

A LeetCode account

A Gmail account (or any other email provider) to send emails from.

Important for Gmail: You will need to generate an "App Password" to use for sending emails. You can find instructions here.

1. Clone the Repository
Bash

git clone https://github.com/your-username/leet-code-automation.git
cd leet-code-automation
2. Install Dependencies
It's recommended to use a virtual environment.

Bash

# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Install the required packages
pip install -r requirements.txt
(Note: You will need to create a requirements.txt file with libraries like requests and python-dotenv.)

3. Configuration
This project uses environment variables to handle your secret keys and tokens securely.

Create a file named .env in the root of the project directory.

Copy the contents of .env.example into your new .env file.

Code snippet

# .env.example

# LeetCode API Credentials
LEETCODE_SESSION="YOUR_LEETCODE_SESSION_COOKIE"
CSRF_TOKEN="YOUR_CSRF_TOKEN"

# Email Configuration
SENDER_EMAIL="your_email@gmail.com"
SENDER_PASSWORD="YOUR_GMAIL_APP_PASSWORD" # Not your regular password!
RECEIVER_EMAIL="your_personal_email@example.com"
Fill in the values in your .env file.

How to get LEETCODE_SESSION and CSRF_TOKEN:
Log in to your LeetCode account in your web browser.

Open the browser's Developer Tools (usually by pressing F12 or Ctrl+Shift+I).

Go to the Network tab.

Refresh the page or click on any problem. Find a request made to https://leetcode.com/graphql.

Click on this request and look at the Request Headers section.

Find the cookie header. Inside, you will see LEETCODE_SESSION=...; and csrftoken=...;.

Copy the corresponding values and paste them into your .env file.
