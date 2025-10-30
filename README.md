# PHP Guestbook - Codespace Edition

A simple guestbook application built with PHP and MariaDB, configured to run in GitHub Codespaces or any dev container environment.

## Features

- Create, read, update, and delete guestbook entries
- Simple PHP application with MySQL/MariaDB backend
- Fully containerized development environment
- Pre-configured for GitHub Codespaces

## Quick Start with GitHub Codespaces

1. Click the **Code** button on this repository
2. Select the **Codespaces** tab
3. Click **Create codespace on main** (or your branch)
4. Wait for the codespace to build (this may take a few minutes on first run)
5. Once ready, the application will be available at the forwarded port 8080
6. Click the **Ports** tab in VS Code and open the port 8080 URL
7. You should see the guestbook application running!

## Running Locally with Dev Containers

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

### Steps

1. Clone this repository:
   ```bash
   git clone https://github.com/TonyJenkins/guestbook-php-codespace.git
   cd guestbook-php-codespace
   ```

2. Open in VS Code:
   ```bash
   code .
   ```

3. When prompted, click **Reopen in Container** (or press F1 and select "Dev Containers: Reopen in Container")

4. Wait for the container to build and start

5. Access the application at `http://localhost:8080`

## Application Structure

- `index.php` - Main page displaying all guestbook entries
- `insert.php` - Handles new entry creation
- `update.php` - Form for editing existing entries
- `process_update.php` - Processes entry updates
- `delete.php` - Handles entry deletion
- `connect.php` - Database connection configuration
- `guestbook.sql` - Database schema and initial data
- `css/` - Stylesheets
- `img/` - Images and assets

## Database Configuration

The dev container automatically sets up a MariaDB database with the following credentials:

- **Host**: `db` (within container network)
- **Database**: `guestbook`
- **User**: `guestbook_user`
- **Password**: `guestbook_password`
- **Root Password**: `root`

The database is automatically initialized with sample data from `guestbook.sql`.

## Development

### Accessing the Database

You can connect to the MariaDB database using:

1. **From within the container**:
   ```bash
   mysql -h db -u guestbook_user -pguestbook_password guestbook
   ```

2. **From your host machine** (when running locally):
   - Host: `localhost`
   - Port: `3306`
   - Username: `guestbook_user`
   - Password: `guestbook_password`
   - Database: `guestbook`

### VS Code Extensions

The dev container automatically installs useful extensions:

- PHP Debug (Xdebug)
- PHP Intelephense (code intelligence)
- SQLTools (database management)
- SQLTools MySQL/MariaDB driver

## Troubleshooting

### Application not loading?

1. Check if the services are running:
   ```bash
   docker ps
   ```

2. Check Apache logs:
   ```bash
   tail -f /var/log/apache2/error.log
   ```

### Database connection issues?

1. Verify the database service is healthy:
   ```bash
   docker ps
   ```

2. Test database connection:
   ```bash
   mysql -h db -u guestbook_user -pguestbook_password -e "SELECT 1"
   ```

### Container won't start?

1. Rebuild the container:
   - Press F1 in VS Code
   - Select "Dev Containers: Rebuild Container"

## Credits

Original application by Tony Jenkins: https://github.com/TonyJenkins/guestbook-php

This repository adds dev container configuration for easy deployment in GitHub Codespaces and local dev container environments.