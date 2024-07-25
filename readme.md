# Global Evangelistic Network (GEN) WordPress Website

This repository contains the configuration and setup for the Global Evangelistic Network WordPress website.

## Project Structure

```
.
├── .git
├── .gitignore
├── README.md
├── stack.yml
├── .env.example
└── wp-content
    ├── themes
    ├── plugins
    └── uploads
```

## Prerequisites

- Docker
- Docker Swarm
- Traefik (configured and running)

## Setup

1. Clone this repository:
   ```
   git clone https://github.com/your-organization/gen-wordpress.git
   cd gen-wordpress
   ```

2. Copy the `.env.example` file to `.env` and fill in the necessary environment variables:
   ```
   cp .env.example .env
   ```

3. Deploy the stack:
   ```
   docker stack deploy -c stack.yml gen
   ```

## Configuration

- The WordPress site will be available at `https://gen.my.kipya-connect.com`
- Traefik is configured to handle SSL termination
- WordPress and MariaDB data are persisted in Docker volumes
- The services are constrained to run on a specific node for data persistence

## Theme and Plugins

- Theme: Holy Church (https://themeforest.net/item/holy-church-religion-nonprofit-theme/20249696)
- Required Plugins:
  - Contact Form 7
  - The Events Calendar
  - WPML (for multi-language support)
  - Donation Plugin (e.g., Give - Donation Plugin)

## Maintenance

### Updating WordPress

To update WordPress or plugins, use the WordPress admin interface. If you need to update the Docker image:

1. Update the image version in `stack.yml`
2. Redeploy the stack:
   ```
   docker stack deploy -c stack.yml gen
   ```

### Backups

Regularly backup the `wp_data` and `db_data` volumes. You can use Docker volume backup tools or scripts to automate this process.

## Contributing

Please read CONTRIBUTING.md for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.
