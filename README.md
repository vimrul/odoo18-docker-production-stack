# Odoo 18 Docker Production Stack

This repository contains a fully Dockerized production-ready setup of **Odoo 18** with **PostgreSQL**, secure **Docker secrets**, and support for **custom addons** and configurations.

> ⚙️ Built with best practices for DevOps and designed for easy deployment on any Linux server or cloud environment.

---

## 📦 What's Included

- ✅ Odoo 18 container (official image)
- ✅ PostgreSQL 15 with secure password via Docker secret
- ✅ Custom addons support via mounted volume
- ✅ Mounted configuration directory (`config/`)
- ✅ Persistent named volumes for database and app data

---

## 🚀 Quick Start Guide

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/odoo18-docker-production-stack.git
cd odoo18-docker-production-stack
```

### 2️⃣ Create Required Directories

```bash
mkdir -p addons config
```

### 3️⃣ Set Proper Permissions

> Ensure Odoo has read/write access

```bash
chmod -R 755 addons config
chown -R 1000:1000 addons config
```

### 4️⃣ Create the PostgreSQL Secret File

```bash
echo "odoo123" > odoo_pg_pass
```

> 🔐 Make sure `odoo_pg_pass` is a **file**, not a directory!

---

## 🐳 Run the Stack

Use Docker Compose to build and launch your Odoo stack:

```bash
docker compose up -d
```

✅ Odoo will be accessible at: [http://localhost:8055](http://localhost:8055)

---

## 🛠️ Configuration

- Place your custom `odoo.conf` inside the `config/` directory.
- Add your custom modules inside the `addons/` folder.
- The database name defaults to `postgres`, and user is `odoo`.

### ✅ Example: `config/odoo.conf`

```ini
[options]
addons_path = /mnt/extra-addons
admin_passwd = admin
db_host = db
db_port = 5432
db_user = odoo
db_password = odoo123
log_level = info
```

---

## 🔁 Restart or Rebuild

To restart:

```bash
docker compose restart
```

To rebuild:

```bash
docker compose down -v
docker compose up -d
```

---

## 🧪 Test Access

- Admin Panel: [http://localhost:8055](http://localhost:8055)
- Login credentials:
  - Email: (you create during DB creation)
  - Password: (you define)

---

## 🧠 Tips

- Make sure the `odoo_pg_pass` file **contains the password only**, with **no newlines**.
- Use `docker logs odoo18` to debug issues.
- Always use volumes for database persistence.

---

## ❌ Troubleshooting

| Problem | Solution |
|--------|----------|
| `POSTGRES_PASSWORD is not specified` | Ensure `odoo_pg_pass` exists and is not a directory |
| Cannot login | Use the correct database, or recreate it via the web UI |
| `ir.http` KeyError | Run with `-i base` if DB not initialized |

---

## 📂 Folder Structure

```text
.
├── addons/             # Custom addons here
├── config/             # Odoo configuration files (odoo.conf)
├── odoo_pg_pass        # Docker secret with DB password
├── docker-compose.yml  # Core stack definition
└── README.md           # You’re reading it!
```

---

## 📈 SEO Tags

`odoo 18 docker`, `odoo production deployment`, `odoo docker compose`, `odoo with postgres`, `odoo docker secure setup`

---

## 📄 License

This project is open-source and free to use under the [MIT License](LICENSE).

---

## 🤝 Contribute

Feel free to fork and submit pull requests to improve this stack or extend its functionality (e.g., Nginx reverse proxy, Let's Encrypt SSL, nightly DB backups, etc.).

---

## ✨ Author

**Imrul Hasan**  
DevOps Engineer
Twitter: [@vimrul](https://twitter.com/vimrul)  
Website: [https://imrul.net](https://imrul.net)
