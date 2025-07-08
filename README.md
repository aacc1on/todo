````markdown
# 📝 My To-Do List App

A simple full-stack To-Do List application built with **Node.js**, **Express**, **MongoDB**, and served using **Nginx** on a **VPS**.

## 🚀 Live Demo

Access the live deployed version here:  
🔗 [http://mytodolistdevhack.duckdns.org](http://mytodolistdevhack.duckdns.org)

---

## ✨ Features

- Add new to-do items via a form
- View all saved tasks with "Show All" button
- All tasks are stored persistently in MongoDB
- Clean and minimal frontend with HTML & CSS
- Dynamic task loading using JavaScript (AJAX)
- Fully deployed on a VPS and managed via `pm2`

---

## 🧰 Technologies Used

- Node.js & Express
- MongoDB (local instance)
- HTML / CSS / JavaScript (vanilla)
- PM2 (for background process management)
- Nginx (as reverse proxy)
- DuckDNS (free dynamic domain)

---

## 📦 Installation (Local)

```bash
git clone https://github.com/yourusername/my-todo-app.git
cd my-todo-app
npm install
````

Create a `.env` file:

```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/tododb
```

Then run:

```bash
node server.js
```

Visit: [http://localhost:3000](http://localhost:3000)

---

## ⚙️ VPS Deployment Notes

The app is deployed on a VPS using the following setup:

* **PM2 Process Name:** `hsahakyanproject`
* **Running Port:** `14542`
* **Nginx Configuration:**

```nginx
server {
    listen 80;
    server_name mytodolistdevhack.duckdns.org;

    location / {
        proxy_pass http://localhost:14542;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

---

## 🤝 Multi-Developer VPS Strategy

To avoid conflicts when deploying multiple projects on the same VPS:

* Each user is assigned a **unique port** (e.g., 14542, 14543, …)
* Nginx routes traffic based on domain/subdomain or subpath
* Each app is managed independently with PM2 using unique process names
* Shared documentation helps track port usage and configurations

---







