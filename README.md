# Keycloak IAM Setup

This repository contains a Docker Compose configuration for running Keycloak Identity and Access Management (IAM) service with Nginx as a reverse proxy.

## Environment Setup

1. Copy the `.env.example` file to `.env`:
```bash
cp .env.example .env
```

2. Update the `.env` file with your secure values:
```env
# Database Configuration
DB_DATABASE=keycloakdb
DB_USER=keycloak
DB_PASSWORD=your_secure_db_password

# Keycloak Admin Configuration
KEYCLOAK_ADMIN=admin
KEYCLOAK_ADMIN_PASSWORD=your_secure_admin_password

# Keycloak User Configuration
KEYCLOAK_USER=user
KEYCLOAK_PASSWORD=your_secure_user_password
```

## Running the Service

Start the service using Docker Compose:
```bash
docker-compose up -d
```

The Keycloak admin console will be available at:
- http://localhost (via Nginx reverse proxy)
- http://localhost:8080 (direct Keycloak access)

## Architecture

The setup includes:
- Keycloak IAM service running on port 8080
- Nginx reverse proxy forwarding port 80 to Keycloak
- PostgreSQL database for Keycloak data storage

## Security Notes

- Never commit the `.env` file to version control
- Use strong, unique passwords for all accounts
- In production, enable HTTPS and configure proper SSL certificates
- Regularly update the Keycloak and Nginx images to the latest version 