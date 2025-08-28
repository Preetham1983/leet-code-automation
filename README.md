# 🤖 LeetCode Daily Problem Reminder using n8n

An n8n workflow designed to keep you consistent with your LeetCode daily challenges. This automation checks if you've solved the daily LeetCode problem and sends you an email reminder every two hours until you do.



---

## ## Overview 🎯

We all know consistency is key to mastering data structures and algorithms. However, it's easy to forget the daily LeetCode problem amidst a busy schedule. This project provides a simple, automated solution to that problem.

The workflow, built on the low-code platform **n8n**, runs on a schedule, checks your LeetCode profile, and acts as your personal accountability partner. Once you solve the problem, it stops reminding you for the day.

---

## ## How It Works ⚙️

The workflow follows a simple but effective logic:

1.  **Trigger:** A **Cron** node triggers the workflow every **2 hours**.
2.  **Fetch Problem Status:** An **HTTP Request** node makes a call to the LeetCode GraphQL API to check the status of the daily question for your account.
3.  **Check Completion:** An **IF** node checks the API response to see if the `status` field is "ac" (Accepted).
4.  **Send Reminder:**
    * **If Not Solved:** An **Email** node sends a reminder to your configured email address.
    * **If Solved:** The workflow stops and waits for the next day.

---

## ## Features ✨

* **Automated Nudging:** Get periodic reminders so you never miss a day.
* **Set It and Forget It:** The workflow runs automatically in the background.
* **Smart Stop:** Notifications cease automatically once you've completed the daily problem.
* **Customizable:** Easily change the trigger interval (e.g., every hour) or the notification method (e.g., use Discord, Slack, or Telegram instead of email).
* **Low-Code:** Built with n8n, making it easy to understand, modify, and maintain without extensive coding.

---

## ## Setup 🚀

To get this workflow up and running in your own n8n instance, follow these steps.

### ### Prerequisites

* An active **n8n instance** (either self-hosted or on n8n.cloud).
* Your **LeetCode account** credentials (specifically the session cookie).
* An **email account** to send notifications from (e.g., Gmail, Outlook).

### ### Installation Steps

1.  **Download the Workflow:** Clone this repository or download the `LeetCodeReminder.json` file.
2.  **Import to n8n:** Open your n8n canvas and import the downloaded JSON file.
3.  **Configure Credentials:**
    * **HTTP Request Node:** You need to add your LeetCode session cookie.
        * Log in to LeetCode in your browser.
        * Open the developer tools (F12 or Ctrl+Shift+I).
        * Go to the `Application` (or `Storage`) tab, find Cookies, and look for `https://leetcode.com`.
        * Find the cookie named `LEETCODE_SESSION` and copy its value.
        * In the n8n HTTP Request node, go to the headers and paste the value into the `Cookie` field in the format `LEETCODE_SESSION=your_copied_value;`.
    * **Email Node:** Configure your email credentials. If you are using Gmail, it's highly recommended to use an **App Password** for security.
4.  **Activate the Workflow:** Save the workflow and toggle the "Active" switch to ON.

That's it! Your automated reminder system is now live. 🎉

---

## ## Contributing 🤝

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/YOUR_USERNAME/YOUR_REPO/issues).

---

## ## License 📄

This project is licensed under the MIT License. See the `LICENSE` file for details.
