# System Setup Playbooks

This directory contains a collection of Ansible playbooks designed to set up a development and administrative environment.

**⚠️ Target OS:** These configurations are tailored for **Ubuntu 24.04 (Noble Numbat)**.

## Execution Order

For best results, run these playbooks in the following order:
1.  `setup_apt_packages.yml` (System packages and updates)
2.  `setup_docker.yml` (Docker runtime)
3.  `setup_flatpaks_and_snaps.yml` (Sandboxed app installs)
4.  `setup_user_configs.yml` (User environment customizations)

### 🚀 Execution

To run the entire setup sequence in a single command use:

```bash
ansible-playbook sysadmin-tools.yml -i inventory.yml
```
---

### 📚 Playbook Descriptions

*   **`setup_apt_packages.yml`**: Manages core system packages using `apt`. It updates the cache, performs general system upgrades, removes unused dependencies, and installs a curated list of essential development and utility tools (e.g., `git`, `curl`, `btop`, `flatpak`).
* **`setup_docker.yml`**: Installs Docker runtime on Ubuntu. Adds Docker's official GPG key, configures the Docker repository, installs Docker Engine, CLI, containerd, Buildx, and Compose plugins, then adds the connecting user to the `docker` group.
*   **`setup_flatpaks_and_snaps.yml`**: Handles installation of sandboxed applications. It sets up the Flathub remote and installs applications via both **Flatpak** and **Snap** (e.g., Gradia).
*   **`setup_user_configs.yml`**: Applies per-user tooling and dotfiles driven from the `templates/` directory. Installs **InconsolataGo Nerd Font** under `~/.local/share/fonts`, **Joplin** (upstream install script), and system **Nano** syntax rules for YAML (`yaml.nanorc`). Adds bash prompt helpers and **`starship`**. Configures **Alacritty** by cloning the [`alacritty/alacritty-theme`](https://github.com/alacritty/alacritty-theme) repository into `~/.config/alacritty/themes` and deploying **`alacritty.toml`** so it imports **`themes/themes/monokai.toml`** from that checkout. Sets up **tmux**: installs **TPM** and **`tmux-themepack`** under `~/.tmux/plugins/` (where TPM expects them) and lays down **`~/.tmux.conf`**. Installs **Zed** (`~/.local/bin/zed`) and copies **`settings.json`** into `~/.config/zed`.
