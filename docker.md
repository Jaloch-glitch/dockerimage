

```markdown
# 1. Containerizing an App

Clone the repository

```sh
docker image build -t dockerusername/nameoftherepo:version .
```

This tells Docker to follow the instructions in the Dockerfile to build the image.

Example:

```sh
docker image build -t jalochfelix/gsd:ctr2023 .
```

![alt text](<image.png>)

# 2. Hosting on Registry

Log in to Docker Hub via terminal or the Docker playground

```sh
docker image push jalochfelix/gsd:ctr2023
```

Example below shows how to build one for AMD since I am a Mac OS user:

```sh
docker buildx build \
  --platform linux/arm64/v8,linux/amd64 \
  --push --tag jalochfelix/gsd:ctr2023 .
```

# 3. Running a Containerized App

```sh
docker container run -d --name web -p 8000:8080 \
  jalochfelix/gsd:ctr2023
```

- `-d` tells it to run in the background and detach from the terminal.
- `web` is the name you give to the app. Take note of the name.
- `-p` is port mapping, mapping the port of the app to the playground or local port. Both the playground and local run on port 8000 (host port:container port).

Then you tell it what image to use.

## Check if it is running

```sh
docker container ls
```


# 4. Stopping a container

```sh 
docker container stop web
```

## Chekck if the container actually stopped

```sh
docker container ls -a
```

## Start the container again 

```sh 
docker container start web
```