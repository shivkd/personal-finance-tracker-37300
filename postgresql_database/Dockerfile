# Use official PostgreSQL image
FROM postgres:15

# Set environment variables for initialization
ENV POSTGRES_DB=finance_db
ENV POSTGRES_USER=finance_user
ENV POSTGRES_PASSWORD=finance_password

# Copy initialization SQL script
COPY init.sql /docker-entrypoint-initdb.d/init.sql

# Expose default PostgreSQL port
EXPOSE 5432
