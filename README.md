# 🚀 ClaudeCodeAnywhere Dev Setup (Remote + Secure Workflow)

A personal development setup for interacting with Claude-compatible APIs, using **OpenRouter**, with secure remote access via **Tailscale**, mobile control using **Termius (on phone)**, and an enhanced terminal experience using **Oh My Claude**.

---

## 📦 Overview

This project documents a flexible, cross-platform setup that allows you to:

* Use Claude-compatible APIs through [OpenRouter](https://openrouter.ai)
* Access your machine remotely from anywhere
* Maintain persistent terminal sessions
* Enhance CLI interactions with [Oh My Claude](https://github.com/) (add your repo link here)

---

## 🧰 Tools & Technologies

* [OpenRouter](https://openrouter.ai) – API provider for Claude-compatible models
* [Tailscale](https://tailscale.com) – Secure private network for remote access
* SSH + WSL (Windows) / SSH + tmux (Linux)
* [tmux](https://github.com/tmux/tmux) – Persistent terminal sessions
* [Oh My Claude](https://github.com/yeachan-heo/oh-my-claudecode) – Enhanced CLI experience

---

## ⚙️ Environment Variables

Set these variables depending on your system:

### Windows (CMD)

```cmd
setx ANTHROPIC_BASE_URL "https://openrouter.ai/api"
setx ANTHROPIC_AUTH_TOKEN "YOUR_TOKEN_HERE"
setx ANTHROPIC_API_KEY "NO_NEED"
```

> ⚠️ Restart your terminal after setting variables.

---

### Linux / WSL

Add the following to your shell profile:

```bash
nano ~/.bashrc
```

Then append:

```bash
export ANTHROPIC_BASE_URL="https://openrouter.ai/api"
export ANTHROPIC_AUTH_TOKEN="YOUR_TOKEN_HERE"
export ANTHROPIC_API_KEY="NO_NEED"
```

Apply changes:

```bash
source ~/.bashrc
```

---

## 🖥️ Windows Setup

### 1. Install OpenSSH Server

Run in **PowerShell (Admin)**:

```powershell
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
Start-Service sshd
Set-Service -Name sshd -StartupType Automatic
```

---

### 2. Allow SSH through firewall

```powershell
New-NetFirewallRule -Name sshd -DisplayName "OpenSSH Server" -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

---

### 3. Install WSL (recommended)

```cmd
wsl --install
```

Inside WSL:

```bash
sudo apt update
sudo apt install tmux -y
```

---

## 🐧 Linux Setup

### 1. Install dependencies

```bash
sudo apt update && sudo apt install openssh-server tmux -y
```

---

### 2. Enable SSH

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

---

## 🔐 Secure Remote Access with Tailscale + Termius

1. Install [Tailscale](https://tailscale.com/download) on both your Windows/Linux machine and your phone
2. Log in using the same account on all devices
3. Get your private Tailscale IP:

```bash
100.x.x.x
```

4. Install and use [Termius](https://termius.com) on your phone

   * Open Termius
   * Create a new host:

     * **Host**: your Tailscale IP (e.g. `100.x.x.x`)
     * **Username**: your Windows/Linux username
     * **Password**: your system password (or SSH key if configured)
   * Save and connect

5. Connect using SSH through Termius:

```bash
ssh user@100.x.x.x
```

💡 Termius gives you a clean mobile terminal UI, saved connections, and easy reconnects.

---

## 🧠 Persistent Terminal (tmux)

Start a session:

```bash
tmux new -s main
```

Detach:

```bash
Ctrl + B, then D
```

Reattach:

```bash
tmux attach -t main
```

---

## 💡 Workflow

1. Connect from your phone using Termius over Tailscale
2. SSH into your machine
3. Start a tmux session
4. Run your tools, scripts, or workflows
5. Detach and reconnect anytime without losing state

---

## 🎯 Features

* 🔒 Secure private access via Tailscale
* 💻 Cross-platform (Windows + Linux)
* 🔁 Persistent terminal sessions
* ⚡ API flexibility via OpenRouter
* 🧩 Enhanced CLI experience

---

## 📌 Disclaimer

This project is a personal development setup intended for legitimate use with API providers and infrastructure you own or control.

---

## 🤝 Credits

* [OpenRouter](https://openrouter.ai)
* [Tailscale](https://tailscale.com)
* [tmux](https://github.com/tmux/tmux)
* [OpenSSH](https://www.openssh.com)
* [Oh-My-Claude](https://github.com/yeachan-heo/oh-my-claudecode)

---

⭐ If you found this useful, consider giving the repo a star!
