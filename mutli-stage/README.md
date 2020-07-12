# Multi-stage Dockerfile

## Misc Commands

- `docker image ls` - list all images
- `docker image prune` - cleans up image list. Add `-a` to get a fresh slate
- `docker ps -a` - list all running images (even stopped). If you want to rerun an image with the same name you will have to remove it first (even if it is stopped)
- `docker system prune` - cleans up both containers and images(?). Add `-a` for a completely clean slate.

## Production

### Build production image

`docker build -t nodemulti:prod --target prod .`

### Run production image

`docker run --init -d -p 80:3000 --name prod nodemulti:prod`

### Test production is working

- go to localhost on browser

### Production clean up

- `docker stop prod`
- OR `ctr+c` if not detached
- `docker rm prod`

## Development

### Build dev image

`docker build -t nodemulti:dev --target dev .`

### Run dev image

`docker run --init -p 80:3000 --name dev nodemulti:dev`

### Test dev is working

- go to localhost on browser

### Dev clean up

- `ctr+c`
- `docker rm dev`

## Test

### Build test image

`docker build -t nodemulti:test --target test .`

### Run and test, test image

`docker run --name test nodemulti:test`

### Test clean up

- `ctr+c`
- `docker rm test`
