# Ubuntu Dev Environment with SSH in Docker

This project sets up a **production-ready Linux development environment** on Windows using Docker. It provides an Ubuntu container with SSH access, essential development tools, and Visual Studio Code integration.

## Features

- Ubuntu-based Docker container
- SSH server enabled (port 2222 on host)
- User `vishal` with sudo privileges
- Pre-installed development tools: `g++`, `gcc`, `cmake`, `vim`, `curl`, `build-essential`
- Workspace folder mounted for code sharing
- VS Code Dev Container support for seamless development

## Getting Started

### 1. Build the Docker Image

```sh
docker build -t ubuntu-ssh .
```

### 2. Start the Container

```sh
docker-compose up -d
```

This will start the container and map:

- Host port `2222` → Container port `22` (SSH)
- `./workspace` folder → `/home/vishal/workspace` in the container

### 3. Connect via SSH

```sh
ssh vishal@localhost -p 2222
# Password: vishal1234
```

### 4. Open in VS Code

- Install the [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension.
- Open the project folder in VS Code.
- Click "Reopen in Container" when prompted.

## File Structure

- `Dockerfile` — Defines the Ubuntu image with SSH and dev tools.
- `docker-compose.yml` — Runs the container with correct ports and volumes.
- `.devcontainer/devcontainer.json` — VS Code Dev Container configuration.
- `workspace/` — Your code and projects go here.

## Security Notes

- **Change the default password** for user `vishal` before using in production.
- **Disable root SSH login** and consider using SSH keys for authentication.
- This setup is for development. For production, further hardening is recommended.

---

Happy