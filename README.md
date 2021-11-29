# Monitoring with Checkmk and Docker

### ERROR: Pool overlaps with other one on this address space

- run: `docker network prune`

- Rebuild Container

------------------------

### Build Container

```
docker-compose -f "docker-compose.yml" up -d --build
```

-------------------------

### Add postgres to monitoring

- "Setup" > "Hosts" > "Add hosts to the monitoring"
- Hostname -> `checkmk_postgres_1`
- "Save & go to service configuration"
- wait for scan
- click on "X Changes" on top right
- "Acitvate on selected sites"