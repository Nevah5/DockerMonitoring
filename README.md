# Monitoring with Checkmk and Docker

## Overview
- Errors
    - ["Pool overlaps with other one on this adress space"](https://github.com/nevah5/dockerMonitoring/#error-pool-overlaps-with-other-one-on-this-address-space)
- Container
    - [Build Container](https://github.com/nevah5/dockerMonitoring/#build-container)
- Monitoring
    - [Add hosts](https://github.com/nevah5/dockerMonitoring/#add-host-system-to-monitoring)
    - [Add a monitoring rule](https://github.com/nevah5/dockerMonitoring/#add-a-monitoring-rule-for-postgres)
    - [Monitor Postgres database](https://github.com/nevah5/dockerMonitoring/#monitor-postgres-database-with-this-container)
- Other
    - [Bash access](https://github.com/nevah5/dockerMonitoring/#bash-access)
    - [Database access](https://github.com/nevah5/dockerMonitoring/#database-access)
    - [Container network diagram](https://github.com/nevah5/dockerMonitoring/#network-diagram)
------------------------
### ERROR: Pool overlaps with other one on this address space
+ run: `docker network prune`
+ Rebuild Container
------------------------
### Build Container
```
docker-compose -f "docker-compose.yml" up -d --build
```
or open folder in VSC, (if you have docker extension) right click on `docker-compose.yml` and click `Compose Restart`

-------------------------
### Add Host System to monitoring
+ "Setup"
+ "Hosts"

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/1.png">

+ "Add hosts to the monitoring"

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/2.png">

+ Hostname -> `localhost`

+ "Save & go to service configuration"

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/3.png">

+ Add every service

+ Click on Changes in top right

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/4.png">

+ "Activate on selected sites"

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/5.png">

--------------------------
### Add a monitoring rule for postgres
+ "Setup"
+ "Services"
+ "Service Monitoring rules"
+ <kbd>CTRL</kbd> + <kbd>F</kbd> "PostgreSQL Database Statistics"
+ Select this option
+ "Create Rule in Folder: Main directory"
+ Set "postgres" as description
+ Under Value enable every option and set prefered values

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/7.png" alt="those options">

+ Add every Host that hosts the postgres database to "Explicit Hosts"
+ Re-run a Full Service Scan on the host the database is on

--------------------------
### Monitor Postgres Database with this container
+ Make sure you downloaded [psql] on **default location** (version 14.1 as of current time)
+ Only install the Command Line Tools!

<img height="auto" width="50%" src="https://github.com/Nevah5/DockerMonitoring/raw/images/6.png" alt="This option here!">

+ Make sure your host system has the Windows agent installed under **default location** (should be `C:\ProgramData\checkmk\`), you can find and download the installer under `localhost:8080` when the container is running, in `Setup > Agents > Windows > .msi`
+ download [this python script] at `C:\ProgramData\checkmk\agent\plugins\mk_postgres.py`
+ make sure you have [python] installed and run this script in a console opened at the directory this script is saved with `my_postgres.py`

--------------------------
### Bash access
+ run `docker ps` to see active docker containers
+ copy container ID
+ run `docker exec -it <id> bash` (replace "\<id>" with container ID) or instead of id use `checkmk_<hostname>_1`

### Database access
+ go on site `localhost:8081`
+ server: `192.10.100.3`
+ username: `postgres`
+ password: `<empty>`
+ databse: `<empty>`
--------------------------
### Network Diagram
|Name|Hostname|IPv4|Ports|Function|
|-|-|-|-|-|
|Checkmk|checkmk|192.10.100.2|8080 & 5000|Monitoring|
|Postgres|postgres|192.10.100.3|5432|Database|
|Adminer|adminer|192.10.100.4|8081 & 8080|User Interface|
|Host System|localhost|127.0.0.1|6556|Client System|


[psql]:https://www.enterprisedb.com/downloads/postgres-postgresql-downloads
[this python script]:https://github.com/jrghde/postgresmonitoring/blob/main/mk_postgres.py
[python]:https://www.microsoft.com/en-us/p/python-39/9p7qfqmjrfp7?activetab=pivot:overviewtab
