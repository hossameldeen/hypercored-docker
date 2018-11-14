# hypercored

A daemon that can download and share multiple hypercores and hyperdrives. Supports seeding them to the browser over WebSockets as well.
Backed by [hypercore-archiver](https://github.com/mafintosh/hypercore-archiver)

```
npm install -g hypercored
```

## Usage

``` js
# will watch ./feeds and store data in ./archiver
hypercored
```

For more info run

```
Usage: hypercored [key?] [options]

    --cwd         [folder to run in]
    --websockets  [share over websockets as well]
    --port        [explicit websocket port]
    --no-swarm    [disable swarming]
```

## Docker

1. Install [Docker](http://docker.com/). If you're on Linux, remember to [configure Docker to start on boot](https://docs.docker.com/install/linux/linux-postinstall/). Don't know of the equivalent for other systems.

2. Create a file called `feeds`.

2. In the project root, run this command:

```
docker build -t hypercored:latest . && docker run -d --name=hypercored --restart=always -p 3282:3282 -v ./feeds:/usr/src/app/feeds -v ./archiver:/usrc/src/app/archiver hypercored:latest
```

**Notes:**  
1. Not an expert in Docker security or configuration.  
2. if you have Beaker on the same machine, you may want to change the dat port `-p 3282:3282` to something like `-p 9999:3282`.  
3. To debug the running container:
   - Run `docker ps -a` to see the container running status.  
   - Run `docker logs hypercored` to see the logs.
   - Run `docker exec -it hypercored sh` to get into a terminal.

## License

MIT
