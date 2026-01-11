# 🤖 Ultimate WhatsApp AI Automation Bot (Production v75)

Welcome to the **most advanced, self-healing, and free** WhatsApp Automation System running entirely on **GitHub Actions**. This system integrates **n8n (Automation)**, **WhatsApp (Baileys)**, and **Free AI (g4f)** into a single powerful workflow.

---

## 🌟 Key Features
* **100% Free Hosting:** Runs on GitHub Actions (Zero cost).
* **24/7 Uptime Loop:** Automatically restarts every 6 hours (Handover Logic).
* **Crash Proof:** Uses SQLite WAL mode + Self-Healing Observer.
* **Anti-Ban Technology:** Browser Spoofing, Human Typing Delays, and Queue System.
* **Media Support:** Send Text, Images, Videos, and Audio.
* **Smart Backups:** Auto-syncs data to Supabase & Telegram.

---

## 🛠️ Step 1: Create Necessary Accounts

Before touching the code, create these 5 free accounts and save their details.

### 1. GitHub (The Host)
* Create a new account at [github.com](https://github.com).
* Create a **New Private Repository** (e.g., `my-wa-bot`).

### 2. Ngrok (The Tunnel)
* Sign up at [ngrok.com](https://ngrok.com).
* Go to **Dashboard** → **Your Authtoken**. Copy it.
* Go to **Cloud Edge** → **Domains** → Create a free static domain (e.g., `my-bot-123.ngrok-free.app`).

### 3. MongoDB Atlas (Session Storage)
* Sign up at [mongodb.com](https://www.mongodb.com/cloud/atlas).
* Create a free **Shared Cluster**.
* Go to **Network Access** → Add IP Address → **Allow Access from Anywhere (0.0.0.0/0)**.
* Go to **Database Access** → Create a User (Role: Atlas Admin).
* **Get Connection String:** Click "Connect" → "Drivers" → Copy URL (Replace `<password>` with your user password).

### 4. Supabase (Data Backup)
* Sign up at [supabase.com](https://supabase.com).
* Create a New Project.
* Go to **Storage** (Left Sidebar) → Create a new Bucket named `bot-storage`. **(Make it Private)**.
* Go to **Project Settings** → **API**.
    * Copy **Project URL**.
    * Copy **service_role** Key (Secret).

### 5. Telegram (Notifications)
* Open Telegram app.
* Search for **@BotFather** → Send `/newbot` → Get **Bot Token**.
* Search for **@userinfobot** → Get your numeric **User ID**.

---

## 🔐 Step 2: Setup GitHub Secrets

Go to your **GitHub Repository** → **Settings** → **Secrets and variables** → **Actions**.
Click **"New repository secret"** and add these EXACT names:

| Secret Name | Value to Paste | Description |
| :--- | :--- | :--- |
| `GH_PAT` | `ghp_xxxx...` | Your Personal Access Token (Settings -> Developer Settings -> Tokens -> Classic -> Scope: Workflow). |
| `MONGODB_URI` | `mongodb+srv://...` | Connection string from Step 1.3. |
| `N8N_ENCRYPTION_KEY` | `any-random-password` | Password to encrypt n8n credentials. |
| `NGROK_DOMAIN` | `my-bot.ngrok-free.app` | Your static domain from Step 1.2 (No http://). |
| `NGROK_TOKEN` | `2AmX...` | Authtoken from Step 1.2. |
| `SUPABASE_SERVICE_ROLE` | `eyJhbG...` | "service_role" key from Step 1.4. |
| `SUPABASE_URL` | `https://xyz.supabase.co` | Project URL from Step 1.4. |
| `TELEGRAM_BOT_TOKEN` | `1234:ABC...` | From BotFather. |
| `TELEGRAM_CHAT_ID` | `987654321` | From UserInfoBot. |

---

## 🚀 Step 3: Deployment

1.  In your Repo, create a new file path: `.github/workflows/main.yml`.
2.  **Paste the "Production v75" code** provided by the AI.
3.  Click **Commit Changes**.
4.  Go to the **Actions** tab.
5.  Select **"Production v75"** on the left sidebar.
6.  Click **Run workflow**.

---

## 📱 Step 4: Connecting WhatsApp

1.  Wait 2-3 minutes.
2.  You will receive a message on Telegram: **"🟢 System v75 Online"**.
3.  Open your browser and visit: `https://YOUR-NGROK-DOMAIN/qr`
    * *Example:* `https://my-bot-123.ngrok-free.app/qr`
4.  Open WhatsApp on your phone → **Linked Devices** → **Link a Device**.
5.  Scan the QR Code.
6.  **Done!** Your bot is now live.

---

## 📡 Step 5: API Endpoints (How to Use)

You can use these endpoints inside **n8n (HTTP Request Node)** or any other tool.

### 1. Send Text Message
* **URL:** `http://wa-bot:10000/send`
* **Method:** `POST`
* **JSON Body:**
    ```json
    {
      "number": "919876543210",
      "message": "Hello from GitHub Actions!"
    }
    ```

### 2. Send Image 📸
* **URL:** `http://wa-bot:10000/send`
* **Method:** `POST`
* **JSON Body:**
    ```json
    {
      "number": "919876543210",
      "type": "image",
      "url": "[https://example.com/cat.jpg](https://example.com/cat.jpg)",
      "caption": "Look at this cat!"
    }
    ```

### 3. Send Video 🎥
* **URL:** `http://wa-bot:10000/send`
* **Method:** `POST`
* **JSON Body:**
    ```json
    {
      "number": "919876543210",
      "type": "video",
      "url": "[https://example.com/video.mp4](https://example.com/video.mp4)",
      "caption": "Watch this!"
    }
    ```

### 4. Send Audio 🎵
* **URL:** `http://wa-bot:10000/send`
* **Method:** `POST`
* **JSON Body:**
    ```json
    {
      "number": "919876543210",
      "type": "audio",
      "url": "[https://example.com/audio.mp3](https://example.com/audio.mp3)"
    }
    ```

### 5. Chat with AI (g4f) 🧠
* **URL:** `http://ai-server:5000/chat`
* **Method:** `POST`
* **JSON Body:**
    ```json
    {
      "message": "Write a poem about coding."
    }
    ```
* **Response:** `{"response": "Coding is art..."}`

---

## 📥 Receiving Messages (n8n Setup)

To process incoming WhatsApp messages in n8n:

1.  Open n8n Dashboard (`https://YOUR-NGROK-DOMAIN/workflow`).
2.  Add a **Webhook Node**.
3.  Set Method: `POST`.
4.  Set Path: `/webhook/whatsapp`.
5.  **Activate** the workflow.
6.  Now, when someone messages your bot, n8n will trigger automatically!

---

## ❓ FAQ & Troubleshooting

**Q: Does it work if I close my laptop?**
A: **Yes.** It runs on GitHub's cloud servers, not your laptop.

**Q: What if I log out from WhatsApp on my phone?**
A: The bot will detect the logout, automatically **delete** the database, restart, and show a new QR code at `/qr` for you to scan again.

**Q: How do I stop the bot?**
A: Go to GitHub Actions -> Click the running workflow -> Click **"Cancel run"**. The bot will save your data and stop safely.

**Q: Will I get banned?**
A: Risk is very low. The bot uses "Human Typing Delays", "Queue System", and "Browser Spoofing" to look like a real PC user. **Do not spam 1000s of strangers.**

**Q: Where is my data?**
A: Your n8n workflows and history are saved in **Supabase** (`database.sqlite`). Even if GitHub deletes the server, your data is restored in the next run.
