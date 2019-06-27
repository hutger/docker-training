![docker-logo-150x150.png](https://www.zencode.nl/wp-content/uploads/2015/05/docker-logo-150x150.png)

# Day 4 - LAB - Networking



**Objetives:**

- Deploy a REDIS database
- Build a node.js container app;
- Run the node.js app that will be linked to REDIS DB and exposing port 3000 externally;
- Test the application

 

___



1. At Day-4 folder, **access subfolder** **node-app** and list the files: 

 ```bash
$ ls

Dockerfile  package.json  redis-client.js  server.js
 ```



2. Take a look on Dockerfile content in order to understanding the app requirements:

```Dockerfile
FROM node:9-alpine
WORKDIR '/var/www/app'
COPY . .
ENV REDIS_URL=redis://cache
ENV NODE_ENV=development
ENV PORT=3000
EXPOSE 3000
CMD sh -c 'npm i && node server.js'
```



3. **Build** the *node-app* image:

```bash
$ docker build -t node-app:0.1 .

```

4. **Deploy** a REDIS container, naming it **cache**:

```bash
$ docker run --name cache -d redis

```

5. **Check the Dockerfile** content      and then build the image (publishing port **3000** and **linking** it to REDIS container):

 ```bash
$ docker run -d --name node-app -p 3000:3000 --link cache node-app:0.1
 ```



6. Check the app is running on the container:

 ```bash
$ curl localhost:3000
 ```



7. Using a browser, **open the URL** below pointing to **Docker host IP** address:

>  http://<DOCKER_HOST_IP>:3000/store/nutanix\?docker\=rocks

Adding a entry ***nutanix*** setting a key called ***docker*** to a value ***rocks***.



8. **Get** the entry previously created:

> http://<DOCKER_HOST_IP>:3000/nutanix



____

