# 📝 TextPad Workers

A minimalist web notepad running on Cloudflare Workers/Pages.

![Demo](https://img.shields.io/badge/Demo-Live-success)
![License](https://img.shields.io/badge/License-MIT-blue)

## ✨ Features

- 🚀 **Auto-save** - No save button needed
- 🌙 **Dark mode** - Toggle with one click
- 📱 **Mobile friendly** - Works on all devices
- 🔗 **Shareable** - Every note has a unique URL
- ⌨️ **CLI support** - Access via `curl` or `wget`
- 💾 **Download** - Export as .txt file
- 📧 **Email** - Send via email
- 🗑️ **Delete** - Permanent deletion

## 🚀 Quick Deploy

### Step 1: Fork this repository

Click the **"Fork"** button on GitHub.

### Step 2: Connect to Cloudflare

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Click **Workers & Pages** → **Create application**
3. Select **Pages** → **Connect to Git**
4. Choose your forked repository
5. Configure:
   - Framework preset: `None`
   - Build command: `echo "No build needed"`
   - Build output directory: `/`
6. Click **Save and Deploy**

### Step 3: Create KV Namespace

1. In Cloudflare Dashboard, go to **Workers & Pages** → **KV**
2. Click **Create a namespace**
3. Name: `NOTES`
4. Copy the **Namespace ID**

### Step 4: Bind KV to your project

1. Go to your Pages project → **Settings** → **Functions**
2. Find **KV namespace bindings**
3. Click **Add binding**:
   - Variable name: `NOTES`
   - KV namespace: Select `NOTES`
4. Save

### Step 5: Update wrangler.toml

Edit `wrangler.toml` in your GitHub repo:
```toml
[[kv_namespaces]]
binding = "NOTES"
id = "paste-your-namespace-id-here"

textpad-workers/
├── src/
│   └── index.js          # 主代码（Workers/Pages 入口）
├── wrangler.toml         # Cloudflare 配置
├── README.md             # 说明文档
├── LICENSE               # MIT 许可证
└── .gitignore            # Git 忽略文件
