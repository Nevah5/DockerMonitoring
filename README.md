# Monitoring with Checkmk and Docker
### ERROR: Pool overlaps with other one on this address space
- run: `docker network prune`
- Rebuild Container
------------------------
### Build Container
```
docker-compose -f "docker-compose.yml" up -d --build
```
or open folder in VSC, (if you have docker extension) right click on `docker-compose.yml` and click `Compose Restart`

-------------------------
### Add Host System to monitoring
- "Setup"<br>
- "Hosts"<br>
<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/1.png">
- "Add hosts to the monitoring"<br>
<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/2.png">
- Hostname -> `localhost`<br>
- "Save & go to service configuration"<br>
<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/3.png">
- Add every service<br>
- Click on Changes in top right<br>
<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/4.png">
- "Activate on selected sites"<br>
<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/5.png">

--------------------------
### Default Access
Postgres:<br>
`admin`<br>
`12345`<br>

--------------------------
### Bash access
- run `docker ps` to see active docker containers
- copy container ID
- run `docker exec -it <id> bash` (replace "\<id>" with container ID) or instead of id use `checkmk_<hostname>_1`

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
