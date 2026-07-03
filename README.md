# VPN Command Wrapper

A Python script to solve network issues in China by wrapping any command through a Shadowsocks VPN proxy.

---

## 🎯 Problem

In China, the Great Firewall (GFW) blocks:
- GitHub and AUR access
- Package downloads
- `makepkg -si` gets stuck

**This script fixes it.**

---

## 📦 Quick Install

```bash
# Step 1: Install dependencies
sudo pacman -S shadowsocks-rust python3 curl

# Step 2: Download the script
sudo curl -o /usr/local/bin/vpn https://raw.githubusercontent.com/hishamcyber/vpn-command/main/vpn

# Step 3: Make it executable
sudo chmod +x /usr/local/bin/vpn

# Step 4: Verify installation
vpn

# Step 5: Save your subscription
vpn "https://your-subscription-link-here"

# Step 6: Find the fastest server
vpn --fastest

# Step 7: Start using it!
vpn yay -S google-chrome
```

Now use `vpn` as a command:
```bash
vpn "https://your-subscription-link"
vpn --fastest
vpn yay -S google-chrome
```

---

## 🚀 Commands

| Command | Description |
|---------|-------------|
| `vpn "https://..."` | Save subscription servers |
| `vpn --list` | Show all servers |
| `vpn --test` | Test server speeds |
| `vpn --fastest` | Auto-select fastest server |
| `vpn --select 3` | Manually pick server #3 |
| `vpn <command>` | Run any command through VPN |

---

## 📝 Examples

### Install AUR Package
```bash
# Without VPN (fails in China)
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si  # ❌ Stuck!

# With VPN (works)
vpn git clone https://aur.archlinux.org/yay.git
cd yay
vpn makepkg -si  # ✅ Success!
```

Here's the cleaned-up version for your README:

---

## 🌐 **VPN Setup in Brave Browser**

### 1. Install v2rayA
```bash
vpn yay -S v2raya-bin
vpn sudo systemctl enable --now v2raya
```

### 2. Open v2rayA GUI
```bash
http://localhost:2017
```
Import your subscription servers and start the proxy.

### 3. Install Proxy Extension
Open Brave and go to:
```
vpn brave https://chromewebstore.google.com/detail/proxy-switcher/icpgekloenpkdgbbjnmjddbcmjglflkj
```
Click **"Add to Brave"**.

### 4. Configure Extension
- Click the extension icon → **"Options"**
- Create a new profile:
  - **Name:** `v2rayA`
  - **Protocol:** `SOCKS5`
  - **Server:** `127.0.0.1`
  - **Port:** `20170`
- Click **"Connect"**

**Now you have VPN in Brave!** 🔒

---

## ⚙️ How It Works

- Starts `sslocal` (Shadowsocks client) on `127.0.0.1:1080`
- Sets `http_proxy`, `https_proxy`, `all_proxy` environment variables
- Runs your command through the SOCKS5 proxy
- Proxy stops when command finishes

---

## 📁 Config Files

All stored in `~/.config/vpnrun/`:

| File | Purpose |
|------|---------|
| `nodes.txt` | All saved servers |
| `selected.txt` | Currently selected server |
| `sslocal.pid` | Proxy process ID |

---

## 📋 Dependencies

```bash
sudo pacman -S shadowsocks-rust python3
```

---

## ❓ FAQ

**Q: How do I get a subscription link?**  
A: Sign up with a Shadowsocks provider. (ikuuu.win, etc)

**Q: Why use `-bin` packages?**  
A: Pre-compiled binaries install faster and more reliably.

**Q: Can I use this for other distros?**  
A: Yes, but `pacman` commands are Arch-specific.

---

## 📷 Screenshots

### Listing and Selecting Servers
![Listing and Selecting Servers](./screenshots/swappy-20260703_144705.png)

### Installing yay Through VPN
![Installing yay Through VPN](./screenshots/swappy-20260703_145129.png)

---

## 📄 License

MIT License

---

**Made for Arch Linux users in China.** 🇨🇳

