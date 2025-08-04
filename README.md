# 📦 Task 2 – WhatsApp-Driven Google Drive Assistant

This project is an automation system built using **n8n**, which receives commands via **WhatsApp** (Twilio), performs **Google Drive actions**, and optionally uses **OpenAI** to summarize documents. Responses are sent back to WhatsApp.

---

## ✅ Features

- 📲 Accepts WhatsApp commands via Twilio
- 📁 Lists, moves, deletes Google Drive files
- 🤖 Summarizes text content using OpenAI
- 📤 Sends structured response back to WhatsApp
- 🔐 Uses environment variables for security

---

## 🧩 WhatsApp Commands Supported

| Command                        | Action                                 |
|-------------------------------|----------------------------------------|
| `LIST /ProjectX`              | List files in Google Drive folder      |
| `DELETE /ProjectX/file.pdf`   | Delete specific file                   |
| `MOVE /A/file.pdf /B`         | Move file from folder A to B           |
| `SUMMARY /ProjectX`           | Generate AI summary of folder docs     |

---

## 🛠 Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/YOUR_USERNAME/task-2-whatsapp-gdrive.git
cd task-2-whatsapp-gdrive
```

### 2. Create `.env` file

Use `.env.example` for reference. Fill your credentials:

```env
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_WHATSAPP_NUMBER=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
OPENAI_API_KEY=
```

### 3. Start n8n (Local via Docker)

```bash
docker run -it --rm \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  --env-file .env \
  n8nio/n8n
```

Visit `http://localhost:5678` to open n8n UI.

---

### 4. Import Workflow

1. Open n8n
2. Click top-right menu → "Import workflow"
3. Upload `workflow.json` from this folder

---

### 5. Start Testing

- Send WhatsApp messages to Twilio Sandbox number
- You’ll receive Drive responses automatically 🎉

---

## 🧠 Tips

- Add logging nodes to track actions
- Use filters to block dangerous commands (like DELETE ALL)
- Use Google Drive "List" & "Download" nodes for summaries

---

## 📄 License

MIT
