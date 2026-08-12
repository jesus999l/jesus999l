# Docker Services Guide

Docker is useful for Echo's supporting infrastructure: databases, search, web services, and isolated research utilities. It should not be treated as a replacement for the local Echo runtime.

## Check Docker first

```bash
docker --version
docker compose version
docker ps
```

## Storage safety

Docker can consume significant disk space through images, layers, volumes, and build cache. Check before pulling large images:

```bash
df -h /
docker system df
```

Do not run broad cleanup commands on a production or research host without inspecting what will be removed.

Useful inspection commands:

```bash
docker image ls
docker volume ls
docker network ls
docker ps -a
```

## Start a compose project

From the directory containing the intended `compose.yml` or `docker-compose.yml`:

```bash
docker compose config
docker compose up -d
```

Verify:

```bash
docker compose ps
docker compose logs --tail=100
```

Stop without deleting persistent volumes:

```bash
docker compose down
```

## SearXNG example

The Echo research environment has used SearXNG as a local search component. The important operational rule is to verify the actual compose project and configuration before changing it.

```bash
docker ps --format 'table {{.Names}}\t{{.Ports}}\t{{.Status}}'
```

For a local service, test the published endpoint from the host after startup:

```bash
curl -I http://127.0.0.1:8081/ 2>/dev/null || true
```

## Persistence strategy

For research data, distinguish:

```text
container     → disposable runtime
volume        → persistent application data
object store  → large research artifacts / archives
Git           → source, configuration, documentation
```

Do not put large model files, raw media collections, secrets, or database dumps into the profile repository.

## Cloud storage boundary

Cloud object storage can extend the research system without becoming the Echo brain. Keep credentials outside Git, use least-privilege keys, and upload only explicitly selected artifacts.

The profile repository should contain documentation and reproducible instructions, not cloud credentials.

## Cleanup — inspect first

```bash
docker system df
docker container prune --dry-run 2>/dev/null || true
```

If a cleanup command does not support a dry run on the installed Docker version, inspect the resource lists manually before deleting anything.
