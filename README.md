# docker-stacks

Infrastructure-as-code for Docker services running on the **Obtuse** server.

This repository is the **source of truth** for how core services are defined,
deployed, and recovered. Runtime data and container state live elsewhere; this
repo contains only declarative configuration.

---

## Design Philosophy

- **Declarative over imperative**  
  Services are defined in `docker-compose.yml` files, not ad-hoc `docker run` commands.

- **Separation of concerns**
  - `~/git/docker-stacks/` → desired state (this repo)
  - `/mnt/docker/` → persistent container data
  - `~/docker/` → runtime / working directories (where applicable)

- **Bootstrap vs managed services**
  - Bootstrap tooling (e.g. Portainer) is deployed via CLI
  - Application services are managed via Portainer stacks

- **Public-by-default**
  No secrets, credentials, or private keys live in this repository.

---

## Repository Structure

```text
docker-stacks/
├── portainer/
│   └── docker-compose.yml   # Portainer CE bootstrap stack (CLI-managed)
├── plex/                    # (planned) Plex Media Server stack
├── torrents/                # (planned) Torrent isolation stack
├── minecraft/               # (planned) Minecraft server stack
├── README.md
└── .gitignore
