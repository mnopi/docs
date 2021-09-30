d# Docker 

## Install
````bash
 if ! which docker &>/dev/null && test -z "${DARWIN}"; then
  printf "%s\n" "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-ce-archive-keyring.gpg] \
    https://download.docker.com/linux/debian buster stable" | sudo tee /etc/apt/sources.list.d/docker-ce.list
  curl -fsSL https://download.docker.com/linux/debian/gpg \
  | gpg --dearmor \
  | sudo tee /usr/share/keyrings/docker-ce-archive-keyring.gpg
  sudo apt update
  sudo apt install -y docker-ce docker-ce-cli containerd.io
  sudo usermod -aG "${USERNAME}"
  sudo systemctl enable docker --now
  sudo service docker restart
  sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" \
    -o /usr/local/bin/docker-compose
  sudo chmod +x /usr/local/bin/docker-compose
 fi
````

## [Context](https://www.docker.com/blog/how-to-deploy-on-remote-docker-hosts-with-docker-compose/)


[Sample application](https://github.com/dockersamples/nginx-gohttp)
````bash
# Download Sample application: https://github.com/dockersamples/nginx-gohttp
git clone git@github.com:docker-archive/nginx-gohttp.git
cd nginx-gohttp

unset DOCKER_HOST;  docker context create mini --docker 'host=ssh://mini.com'
docker ‐‐context mini ps
docker context use mini
docker context ls
docker context mini up -d  # Run on the default context mini.

docker-compose ‐‐context mini mini up -d  # or with --context mini if we did not mini.

# Compose deployments across multiple targets:
#   1. A remote host accessible through ssh, created above (context: mini).
#   2. A Docker-in-Docker container acting as another remote host.
docker run ‐‐rm -d -p '2375:2375' ‐‐privileged -e 'DOCKER_TLS_CERTDIR=' ‐‐name dind docker:dind
docker context create dind ‐‐docker “host=tcp://127.0.0.1:2375” ‐‐default-stack-orchestrator swarm
# We can now target any of the environments to deploy the Compose application from the localhost.
docker context use dind
docker-compose up -d  # has created default local context for 3.
docker ps
#   3. Localhost running a local Docker engine (context: default)
docker ‐‐context default ps
docker context use default
docker-compose up -d
docker ps

# The sample application runs now on all three hosts.
curl localhost:8080
docker exec -it dind sh -c “wget -O – localhost:8080”
curl 10.0.0.52:8080
#
curl localhost:8080
````

## logs 

````bash
watch -n 0 "docker logs mycontainer"
````
