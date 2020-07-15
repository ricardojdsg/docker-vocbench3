# docker_vocbench3

Docker images for vocbench3 and a separate rdf4j (sesame) repository.

* http://vocbench.uniroma2.it/
* http://rdf4j.org/

## Setting up DEV environment
1.Clone this repository from GitHub.
```bash
git clone https://github.com/ricardojdsg/docker-vocbench3.git
Clonando en 'docker-vocbench3'...
remote: Enumerating objects: 47, done.
remote: Counting objects: 100% (47/47), done.
remote: Compressing objects: 100% (47/47), done.
remote: Total 121 (delta 26), reused 0 (delta 0), pack-reused 74
Recibiendo objetos: 100% (121/121), 38.23 KiB | 78.00 KiB/s, listo.
Resolviendo deltas: 100% (51/51), listo.
```
- Accessing the repository
```bash
cd docker-vocbench3/
```
2. Download image docker Docker Hub 
- have previously installed docker and docker-compose and login in docker hub
 ```bash
 cd docker-vocbench3/
 docker pull ricardojdsg/docker-vocbench3:latest
 ```
- List the docker images
 ```bash 
 docker@docker:~/docker-vocbench3$ docker images
 REPOSITORY                   TAG                 IMAGE ID            CREATED             SIZE
 ricardojdsg/docker-vocbench3 latest              c220712e7e8d        35 minutes ago      256MB

 ```
3. Create docker services with docker-compose file
- have previously installed docker and docker-compose and login in docker hub
 ```bash
 docker@docker:~/docker-vocbench3$ docker-compose up -d
Creating network "docker-vocbench3_default" with the default driver
Building vocbench3
Step 1/10 : FROM openjdk:8-jdk-alpine
.
.
.
Successfully tagged ricardojdsg/vocbench3:latest
 ```

- List the docker images
 ```bash 
 docker@docker:~/docker-vocbench3$ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
ricardojdsg/vocbench3   latest              4ae25eef2fe6        28 seconds ago      342MB
openjdk                 8-jdk-alpine        a3562aa0b991        14 months ago       105MB

 ```

- Check containers, services and ports that are running
 ```bash
 docker@docker:~/docker-vocbench3$ docker-compose ps -a
  Name                 Command               State           Ports         
---------------------------------------------------------------------------
vocbench3   /bin/sh -c sh /app/vocbenc ...   Up      0.0.0.0:1979->1979/tcp

 ```

 ```bash
 docker30@docker30:~/docker-vocbench3$ docker ps -a
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                   PORTS                    NAMES
5f83db327953        ricardojdsg/vocbench3:latest   "/bin/sh -c 'sh /app…"   2 minutes ago       Up About a minute        0.0.0.0:1979->1979/tcp   vocbench3
8f6e0234a274        bbf22e545fb1                   "/bin/sh -c 'curl -L…"   2 hours ago         Exited (7) 2 hours ago                            exciting_mccarthy

 ```
  
4. Verify web applications
- verify web applications on port 1979 vocbench3 in http://IP_HOST:1979/vocbench3/
- verify web applications on port 1979 vocbench3 in http://localhost:1979/vocbench3/


5.Stop and clean the container
 ```bash
 docker-compose down -v
 make clean
 ```
 
- Delete all images from the dockers
 ```bash 
 docker@docker:~/docker-vocbench3$ docker rmi `docker images -q`
 ```
