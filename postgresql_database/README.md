# Personal Finance Tracker PostgreSQL Database

This container provides the PostgreSQL backend for the Personal Finance Tracker app. It includes tables for users, transactions, budgets, categories, and application metadata.

## How to use

### Build and Run with Docker Compose

```bash
docker-compose up --build
```

- Database: `finance_db`
- User: `finance_user`
- Password: `finance_password`
- Port: `5432`

The schema will be initialized automatically (see `init.sql`).

### Database Schema

- **users**: User authentication and profile info.
- **categories**: Transaction categories per user.
- **budgets**: User-defined budgets.
- **transactions**: All user transactions.
- **metadata**: System/application key-value store.

### Persistence

Data is persisted in the `pg_data` Docker volume.

---

**For production, override credentials and use secrets management.**
