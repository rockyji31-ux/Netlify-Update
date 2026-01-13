# 🤖 Ultimate WhatsApp AI Bot  
**Production v90**

Run a **24×7 WhatsApp AI Bot** on **GitHub Actions** using **Ngrok, MongoDB, Supabase, Telegram and n8n** — completely **free**.

---

## 🚀 Features
- WhatsApp Auto Reply  
- AI Chat (g4f)  
- MongoDB Database  
- Supabase Cloud Backup  
- Telegram Notifications  
- n8n Automation  
- GitHub Actions Hosting  

---

## 🔐 Step 0 — Open GitHub Secrets

Open:
```
GitHub Repo → Settings → Secrets and variables → Actions
```
Click **New repository secret** for all keys below.

---

## 🛠 Step 1 — Ngrok

Login: https://dashboard.ngrok.com  
Open **Setup & Installation**

### Add Secrets

| Name | Value |
|------|-------|
| `NGROK_TOKEN` | Your Ngrok Authtoken |
| `NGROK_DOMAIN` | your-domain.ngrok-free.dev |

---

## 🛠 Step 2 — MongoDB Atlas

Your connection string:
```
mongodb+srv://user:<password>@cluster0.abc.mongodb.net/?appName=Cluster0
```

Edit it:
```
mongodb+srv://user:password@cluster0.abc.mongodb.net/wa_bot_db?retryWrites=true&w=majority
```

Save:

| Name | Value |
|------|-------|
| `MONGODB_URI` | Final edited URL |

---

## 🛠 Step 3 — Supabase

Create Storage Bucket:
```
bot-storage
```
Public = OFF

Get keys from **Settings → API**

| Name | Value |
|------|-------|
| `SUPABASE_URL` | Project URL |
| `SUPABASE_SERVICE_ROLE` | service_role key |

---

## 🛠 Step 4 — Telegram

Create bot via **@BotFather**  
Get user ID via **@userinfobot**

| Name | Value |
|------|-------|
| `TELEGRAM_BOT_TOKEN` | Bot token |
| `TELEGRAM_CHAT_ID` | Your Telegram ID |

---

## 🛠 Step 5 — GitHub Token

GitHub → Settings → Developer Settings → Tokens (classic)

Enable: `workflow`

| Name | Value |
|------|-------|
| `GH_PAT` | GitHub Token |
| `N8N_ENCRYPTION_KEY` | Any password |

---

## 🌐 Bot URLs

After workflow starts:

```
https://YOUR-NGROK-DOMAIN/qr
https://YOUR-NGROK-DOMAIN/reset
```

---

## 📤 Send WhatsApp (n8n)

```
POST http://wa-bot:10000/send
```

```json
{
  "number": "919999999999",
  "message": "Hello from n8n"
}
```

---

## 🤖 AI Chat

```
POST http://ai-server:5000/chat
```

```json
{
  "message": "Write a short story"
}
```

---

## ▶️ Run Bot

1. Create:
```
.github/workflows/main.yml
```
2. Paste **Production v90 Workflow**
3. Commit
4. Go to **Actions → Run Workflow**

---

## ✅ DONE

Your **WhatsApp AI Bot** is now live **24×7 on GitHub Actions**.
