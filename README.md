# ![ETK Logo](https://e-talk.xyz/wp-content/uploads/2025/09/Webchain200-x-200-px-2.webp) ETK Web Miner

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)  
[![Website](https://img.shields.io/badge/Website-e--talk.xyz-blue)](https://e-talk.xyz)

Official **ETK (E-Talk Webchain) Mining Widget** – embed ETK mining directly on partner websites with a secure, no-login-required widget.

---

## 🌐 Overview

The **ETK Web Mining Widget** allows partner websites to integrate ETK mining seamlessly. **No login required** – users simply enter their e-talk user ID to start mining immediately. Mining rewards are securely processed by e-talk servers.  

This widget is fully branded and can be embedded on any partner website with minimal setup.

---

## 🚀 Features

- **No Login Required**: Users only need their e-talk user ID
- Fully branded with ETK logo and design  
- Works cross-site with **API Key + Site ID** validation  
- Configuration bound to domain and protected by admin password  
- Users mine ETK directly on partner websites without authentication
- Mining logic: **370 ETK staked = validator, rewards distributed every 60 minutes**  
- Responsive and mobile-friendly design  
- Secure: API keys protected, no sensitive data exposed to users

---

## 📷 Screenshots

**Widget Preview**  

![Widget Preview](https://e-talk.xyz/wp-content/uploads/2025/09/Screen-Shot-2025-09-27-at-5.19.11-AM.webp)  

**Admin Configuration**  

![Admin Panel](https://e-talk.xyz/wp-content/uploads/2025/09/Screen-Shot-2025-09-27-at-5.11.41-AM.webp)  

---

## 📥 Installation

1. Copy the **embed code** below  
2. Paste it into your website's HTML where you want the widget to appear  
3. Configure your **API Key, Secret, and Site ID** in the admin panel  
4. Save configuration  
5. Visitors can now start mining ETK by entering their user ID

---

## ⚙️ Usage

- **Admin Tab**: Configure API credentials, test connection, and manage your domain access  
- **Widget Tab**: Live preview of mining interface for users  
- **Embed Tab**: Copy the embed snippet for partner websites  

### Example Embed Code (No Login Required)

```html
<!-- ETK Mining Widget (no login required) - yourdomain.com -->
<div id="etk-mining-widget" style="max-width:320px;padding:16px;border-radius:8px;background:#f8f9fa;border:1px solid #eee;text-align:center">
  <img decoding="async" src="https://e-talk.xyz/wp-content/uploads/2025/09/Webchain200-x-200-px-2.webp" alt="ETK" style="width:64px;height:64px;object-fit:contain;border-radius:8px"/>
  <h4 style="margin:8px 0;color:#007cba;font-family:inherit">ETK Mining</h4>
  <div style="font-size:13px;color:#444;margin-bottom:6px">No login required</div>
  <input type="text" id="etk-user-id" placeholder="Enter your e-talk User ID" style="width:100%;padding:8px;border:1px solid #ddd;border-radius:4px;margin-bottom:10px">
  <button onclick="startETKMining()" style="width:100%;padding:10px;background:#007cba;color:white;border:none;border-radius:4px;cursor:pointer">Start Mining</button>
  <div id="etk-mining-status" style="margin-top:10px;font-size:13px"></div>
</div>
<script>
async function startETKMining() {
  const userId = document.getElementById('etk-user-id').value.trim();
  const statusEl = document.getElementById('etk-mining-status');
  
  if(!userId) {
    statusEl.innerHTML = '<span style="color:red">Please enter your user ID</span>';
    return;
  }
  
  statusEl.innerHTML = '<span style="color:green">Starting mining...</span>';
  
  try {
    // Mining API call would go here
    // This uses the site's pre-configured API keys
    const response = await fetch('/api/mine', {
      method: 'POST',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify({userId: userId})
    });
    
    const result = await response.json();
    
    if(response.ok) {
      statusEl.innerHTML = '<span style="color:green">Mining started successfully!</span>';
    } else {
      throw new Error(result.message || 'Mining failed');
    }
  } catch(error) {
    statusEl.innerHTML = '<span style="color:red">Error: ' + error.message + '</span>';
  }
}
</script>
