# Multi-Tenant Authentication Server (Alpha)

Welcome to the Multi-Tenant Authentication Server repository! This server is currently in the alpha stage but is functional. It is designed to be a robust and flexible authentication solution with multi-tenancy support, OAuth2 with OpenID Connect (OIDC), and various authentication methods, including username/password, TOTP, passkeys (YubiKey, etc.), and more. Additionally, the server includes features like permission and role management, making it a comprehensive solution for modern applications.

## Features

- **Multi-Tenant Support:** Serve multiple tenants with isolated authentication and configuration.
- **Multi-Application Per Tenant:** Manage multiple applications within each tenant.
- **OAuth2 and OIDC Support:** Secure authentication using industry-standard protocols.
- **Flexible Authentication Methods:** Support for username/password, TOTP, passkeys (YubiKey, etc.), and more.
- **Permission and Role Management:** Fine-grained access control within applications.
- **Database Support:** Works with SQLite (in-memory or file-based) and PostgreSQL.
- **Cross-Platform:** Available for both Windows and Linux environments.
- **Automatic Certificate Management:** Integrates with Let's Encrypt for automatic HTTPS certificate creation and renewal.

## Getting Started

### Prerequisites

- **Operating System:** Windows or Linux
- **Database:** SQLite or PostgreSQL

### Installation

1. Download the latest release for your platform (Windows or Linux) from the [Releases](#) page.
2. Extract the downloaded ZIP file to your desired directory.

### Configuration

1. Locate the appropriate configuration file for your database setup:

#### Default Configuration (`server.config.yaml`)

```yaml
SERVER_LISTEN: :3000
SERVER_USE_HTTPS: true
SERVER_SECRET: "this is my super secret server password"
USE_SWAGGER: false
AUTO_MIGRATE: true
DB_TYPE: sqlite
DB_CONNECTION_STRING: "file:db.sqlite"
# SQLITE inMemory: file::memory:?cache=shared
# Email configuration
SERVER_EMAIL: "your.server@email.com"
SMTP_HOST: "localhost"
SMTP_PORT: 1025
# SMTP_USER: <user>
# SMTP_PASSWORD: <password>
```

#### PostgreSQL Configuration (server.config.yaml.postgres)

```yaml
SERVER_LISTEN: :3000
SERVER_USE_HTTPS: true
SERVER_SECRET: "this is my super secret server password"
USE_SWAGGER: false
AUTO_MIGRATE: true
# DB Connection string
DB_TYPE: postgres
DB_CONNECTION_STRING: "postgres://postgres:mysecretpassword@localhost:5432/prie_auth_server?sslmode=disable"
DB_MIGRATION_CONNECTION_STRING: "postgres://postgres:mysecretpassword@localhost:5432/prie_auth_server?sslmode=disable"
# Email configuration
SERVER_EMAIL: "your.server@email.com"
SMTP_HOST: "localhost"
SMTP_PORT: 1025
# SMTP_USER: <user>
# SMTP_PASSWORD: <password>
```

#### SQLite Configuration (server.config.yaml.sqlite)

```yaml
SERVER_LISTEN: :3000
SERVER_USE_HTTPS: true
SERVER_SECRET: "this is my super secret server password"
USE_SWAGGER: false
AUTO_MIGRATE: true
DB_TYPE: sqlite
DB_CONNECTION_STRING: "file:db.sqlite"
# SQLITE inMemory: file::memory:?cache=shared
# Email configuration
SERVER_EMAIL: "your.server@email.com"
SMTP_HOST: "localhost"
SMTP_PORT: 1025
# SMTP_USER: <user>
# SMTP_PASSWORD: <password>
```


2. Rename the configuration file you intend to use to server.config.yaml and place it in the same directory as the server binary.
3. Edit the server.config.yaml file to suit your environment and requirements.


### Running the Server

Once the configuration file is updated:

```bash
# On Linux
./auth-server

# On Windows
auth-server.exe
```

The server will start using the specified configuration. By default, it listens on port 3000 for HTTP and 8443 for HTTPS (if configured with a valid certificate).

### TLS/SSL Configuration

The server supports automatic certificate creation and renewal through Let's Encrypt. To enable this, ensure that:

1. The server is bound to port 443.
2. A public DNS record points to the server's IP address.

The server will automatically handle the rest.

### Contributing

The server is currently in alpha but im always looking for feedback. Feel free to add your feedback or questions as issue.


