# Appwrite Self-Hosted Docker Setup

This repository contains Docker Compose configurations for self-hosted Appwrite deployments.

## 🚀 Current Version: 1.9.5 (Main Branch)

The `main` branch contains the latest stable Appwrite version **1.9.5** released on June 30, 2026.

### Features in 1.9.5
- ✨ Presences API for online, typing, and activity states
- 🔢 BigInt columns for Databases
- 🦀 Rust runtime for Functions
- 🐦 X (formerly Twitter) OAuth support
- ⚡ Bun and Deno build runtimes for Sites
- 🔄 Git deployment triggers for Functions and Sites
- 📤 Parallel chunk uploads for faster Storage
- 🔧 Broader migration coverage for project settings

### Important Configuration Notes

**Database Adapter:** Appwrite 1.9.x changed its default database from MariaDB to MongoDB. This setup explicitly configures MariaDB by setting:
```env
_APP_DB_ADAPTER=mariadb
```

## 📦 Version Branches

- **`main`** - Appwrite 1.9.5 (Latest Stable)
- **`v1.8.1`** - Appwrite 1.8.1 (Legacy Version)

## 🛠️ Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/mashunterbd/Appwrite.git
   cd Appwrite
   ```

2. Update environment variables in `.env`:
   ```bash
   # Required: Change these before first run
   _APP_OPENSSL_KEY_V1=your-secret-key-change-this-32ch
   _APP_EXECUTOR_SECRET=your-executor-secret-change-this
   _APP_DB_PASS=appwrite_db_password
   _APP_DB_ROOT_PASS=rootsecretpassword
   ```

3. Start Appwrite:
   ```bash
   docker compose up -d
   ```

4. Access the console:
   ```
   http://localhost/console/
   ```

## 📋 Prerequisites

- Docker Engine 24.0+
- Docker Compose v2.0+
- Minimum 4GB RAM
- 20GB disk space

## 🔧 Configuration

### Environment Variables

Key environment variables in `.env`:

- `_APP_DOMAIN`: Your domain (default: localhost)
- `_APP_OPENSSL_KEY_V1`: Secret encryption key (32 characters)
- `_APP_EXECUTOR_SECRET`: Internal service authentication
- `_APP_DB_ADAPTER`: Database type (mariadb for this setup)
- Database credentials: `_APP_DB_*`
- SMTP settings: `_APP_SMTP_*` (optional)
- Storage settings: `_APP_STORAGE_*`

### Ports

- `80`: HTTP
- `443`: HTTPS

## 📚 Documentation

- [Official Appwrite Docs](https://appwrite.io/docs)
- [Self-Hosting Guide](https://appwrite.io/docs/advanced/self-hosting)
- [Migration Guide](https://appwrite.io/docs/advanced/self-hosting/production/updates)

## 🔄 Upgrading

To upgrade from v1.8.1 to v1.9.5:

1. Backup your data
2. Pull latest changes: `git pull origin main`
3. Stop containers: `docker compose down`
4. Start new version: `docker compose up -d`
5. Run migration: `docker compose exec appwrite migrate`

## 🐛 Troubleshooting

### Database Connection Issues

If you see "Pool is empty" errors, ensure `_APP_DB_ADAPTER=mariadb` is set in your `.env` file.

### Fresh Installation

For a completely fresh install:
```bash
docker compose down -v  # Removes all volumes
docker compose up -d
```

## 📝 License

This configuration is based on the official Appwrite distribution. Appwrite is licensed under the BSD 3-Clause License.

## 🤝 Contributing

For issues or improvements, please open an issue or pull request.

---

**Repository maintained by:** [@mashunterbd](https://github.com/mashunterbd)  
**Last updated:** July 6, 2026
