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

### Database Verification Steps

#### Service Status Check

1. To verify the PostgreSQL container is running:

    ```bash
    docker ps | grep finance_postgres_db
    ```

    The output should list the `finance_postgres_db` container with status `Up` and port `5432/tcp`.

2. To check if the database server is accepting connections:

    ```bash
    docker exec -it finance_postgres_db pg_isready
    ```
    The output should be: `/var/run/postgresql:5432 - accepting connections`

#### Schema Initialization Check

1. To verify tables from init.sql have been created:

    ```bash
    docker exec -it finance_postgres_db psql -U finance_user -d finance_db -c "\dt"
    ```

    This should list tables: users, categories, budgets, transactions, metadata.

2. To check schema for a specific table (example: users):

    ```bash
    docker exec -it finance_postgres_db psql -U finance_user -d finance_db -c "\d users"
    ```

#### Initialization Log Check

- If initialization fails or schema missing, check logs:

    ```bash
    docker logs finance_postgres_db
    ```

    Look for errors related to executing `/docker-entrypoint-initdb.d/init.sql`.

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
