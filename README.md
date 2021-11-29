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

### Database access
- do the above with postgres
- run `psql -U admin`
- enter password
--------------------------
### IPv4 list of containers
|Name|Hostname|IPv4|Ports|Function|
|-|-|-|-|-|
|Checkmk|checkmk|192.10.100.2|8080 & 5000|Monitoring|
|Postgres|postgres|192.10.100.3|5432|Database|
|Adminer|adminer|192.10.100.4|8000 & 7071|Client Database Interface|

--------------------------