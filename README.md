# System Setup Playbooks

This directory contains a collection of Ansible playbooks designed to set up a development and administrative environment.

**⚠️ Target OS:** These configurations are tailored for **Ubuntu 24.04 (Noble Numbat)**.

## Execution Order

For best results, run these playbooks in the following order:
1.  `setup_apt_packages.yml` (System packages and updates)
2.  `setup_flatpaks_and_snaps.yml` (Sandboxed app installs)
3.  `setup_user_configs.yml` (User environment customizations)

### 🚀 Execution

To run the entire setup sequence in a single command use:

```bash
ansible-playbook sysadmin-tools.yml -i inventory.yml
```
---

### 📚 Playbook Descriptions

*   **`setup_apt_packages.yml`**: Manages core system packages using `apt`. It updates the cache, performs general system upgrades, removes unused dependencies, and installs a curated list of essential development and utility tools (e.g., `git`, `curl`, `btop`, `flatpak`).
*   **`setup_flatpaks_and_snaps.yml`**: Handles installation of sandboxed applications. It sets up the Flathub remote and installs applications via both **Flatpak** and **Snap** (e.g., Gradia).
*   **`setup_user_configs.yml`**: Customizes the user environment variables and settings. This includes configuring tools like Starship, Nano, and setting up paths for applications like Zed and Joplin.
