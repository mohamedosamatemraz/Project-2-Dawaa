# 💊 Dawaa (دواء) -- Pharmacy Automation with n8n

Dawaa is a pharmacy automation project built with n8n. A customer asks for
a medicine on WhatsApp (text or a photo of the prescription), an AI agent
reads the request and checks the stock in Google Sheets, and requests that
need a pharmacist reach a Telegram group with Approve and Reject buttons.

## 🌐 Live Website

https://mohamedosamatemraz.github.io/Project-2-Dawaa/

## 🧭 Website Pages

- 🏠 **Home**: project overview and links to WhatsApp, Telegram and GitHub
- 🔴 **Live counter**: WhatsApp chat, n8n execution log and Telegram pharmacist group side by side
- 🗄️ **Back office**: catalog and stock, reservations, error log, scheduled jobs
- 🔄 **Workflows**: architecture and the workflow steps

## ⚠️ Important Note

The Live counter and Back office on the website are a **simulation with sample data**. They follow the logic and the node names of the real workflows, but they do not send real messages. The real system runs in n8n and is reached through the WhatsApp and Telegram buttons on the Home page.

The status badge shows 🟢 Online or 🔴 Offline for the n8n instance, and the WhatsApp and Telegram buttons are disabled when it is offline.

## 🔄 Workflows

| Workflow | Trigger |
| --- | --- |
| 💬 Dawaa-Main (customer) | WhatsApp message |
| 🧑‍⚕️ Dawaa-Main (pharmacist) | Telegram button (callback query) |
| 🚨 Dawaa-Error Handling | Error trigger |
| ⏱️ Dawaa-Error Handling | Schedule: every 15 minutes (expiry check) |
| 🌙 Dawaa-Error Handling | Schedule: every day at 22:00 (low stock) |

## 🛠️ Services and Tools

- ⚙️ n8n: workflow automation
- 📱 WhatsApp Business Cloud API (Meta): customer chat
- ✈️ Telegram Bot: pharmacist approval and team alerts
- 📊 Google Sheets: catalog, reservations and error log
- 📧 Gmail: email alerts and reorder list
- 🧠 AI model: reads text and prescription photos
- 🚇 ngrok: public access to the n8n instance
- 🌍 GitHub Pages: website hosting

## 📥 Import Instructions

1. Download the workflow JSON files from the `workflows` folder.
2. In n8n, create a folder for the project and import each file.
3. Create the credentials (WhatsApp, Telegram, Google Sheets, Gmail, AI) and select them in every node that shows a warning.
4. Replace the Sheet IDs and the Telegram chat ID with your own.
5. In the customer workflow settings, set the error workflow to the Error Handling workflow. Do the same for the other workflows.
6. Activate the workflows. Telegram allows one webhook per bot, so re-activate after using Test workflow.
7. Edit the `CONFIG` object at the top of the script in `index.html`: `n8nBase`, `whatsapp` (international number, digits only), `telegram` (bot username) and `github`.

## 📵 WhatsApp Test Number

The Meta test number only replies to phone numbers added to its allowed list (WhatsApp > API Setup > To > Manage phone number list).

## 🔒 Security

Do not add API keys, tokens, private IDs or personal email addresses to this repository. Configure credentials only inside n8n.
