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
--------------------------
### Default Access
Postgres:<br>
`admin`<br>
`12345`<br>

--------------------------
### Bash access
- run `docker ps` to see active docker containers
- copy container ID
- run `docker exec -it <id> bash` (replace "\<id>" with container ID)
--------------------------
### IPv4 list of containers
|Name|IPv4|Ports|
|-|-|-|
|Checkmk|192.10.100.2|8080 (Webserver) & 5000 (internal)|
|Postgres|192.10.100.3|5432|
|Client (Ubuntu)|192.10.100.4|-|

--------------------------