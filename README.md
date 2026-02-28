# n8n-Workflows-Collection
A collection of ready-to-use n8n automation workflows. Each workflow is self-contained with its own documentation, setup instructions, and exported JSON file ready to import.
# ⚡ n8n Workflows Collection

A collection of ready-to-use [n8n](https://n8n.io) automation workflows. Each workflow is self-contained with its own documentation, setup instructions, and exported JSON file ready to import.

---

## 📦 Workflows

| # | Workflow | Description | Services Used |
|---|----------|-------------|---------------|
|01 |[New Client Onboarding](./workflows/new-client-onboarding/) | Automatically sends a thank-you email to new clients, saves them to Google Contacts, and notifies the owner — triggered by a new row in Google Sheets | Google Sheets, Gmail, Google Contacts |

> More workflows coming soon! ⭐ Star this repo to stay updated.

---

## 🚀 How to Use a Workflow

### Step 1 — Export the JSON
Navigate to the workflow folder you want and download the `workflow.json` file.

### Step 2 — Import into n8n
In your n8n instance:
1. Go to **Workflows** in the sidebar
2. Click **Add Workflow**
3. Click the **⋮ menu** (top right) → **Import from file**
4. Select the downloaded `workflow.json`

### Step 3 — Set up credentials
Each workflow README lists the credentials you need to connect (Google, Gmail, etc.). Set these up under **Settings → Credentials** in n8n.

### Step 4 — Activate
Once credentials are connected and nodes are configured, toggle the workflow to **Active** and you're done!

---

## 🛠️ Requirements

- [n8n](https://n8n.io) — self-hosted or cloud (n8n.cloud)
- Node.js 18+ (for self-hosted)
- Relevant service accounts / API credentials per workflow

---

## 📁 Repo Structure

```
n8n-workflows/
│
├── README.md                        ← You are here
│
├── workflows/
│   └── new-client-onboarding/
│       ├── workflow.json            ← Import this into n8n
│       ├── README.md                ← Setup instructions
│       └── screenshot.png           ← Workflow preview
│
└── assets/
    └── banner.png                   ← Repo banner
```

---

## 🤝 Contributing

Have a workflow to share? Feel free to open a pull request! Please follow the existing folder structure and include:
- `workflow.json` — exported from n8n
- `README.md` — description, setup steps, and credentials needed
- `screenshot.png` — a screenshot of the workflow canvas

---

## 📄 License

MIT — free to use, modify, and share.

---

<p align="center">Built with ❤️ using <a href="https://n8n.io">n8n</a></p>
