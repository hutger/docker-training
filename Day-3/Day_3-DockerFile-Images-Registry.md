![docker-logo-150x150.png](https://www.zencode.nl/wp-content/uploads/2015/05/docker-logo-150x150.png)

# Day 3 - LAB - Dockerfile, Images and Registry



## Building and Running a Flask App

**Objetives:**

- Build a container with a Flask App;
- Tag the image;
- Push the image to a Public Registry;
- Run a Docker container using the previously built Flask image;

 

1. Inside of GIT folder **Day-3**, you'll **find** a folder *python-app* which contains the files below:

```bash
$ ls -la
Dockerfile
index.py
requirements.txt
```



2. In Dockerfile, **update** the image from ***busybox*** to ***python***; 

 ```dockerfile
FROM python
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
EXPOSE 5000
CMD python ./index.py
 ```



3. In *index.py* file, **confirm** if the port is set to 5000;

 ```python
from flask import Flask
app = Flask(__name__)
@app.route("/")
def hello():
  return "Hello World!"
if __name__ == "__main__":
  app.run(host="0.0.0.0", port=int("5000"), debug=True)
 ```

 

4. **Build** the image and make sure that the image is locally stored:

 ```bash
$ docker build -t python-app:0.1 .
$ docker images

 ```

5. **Re-tag** your image setting your Docker Hub repository name:

```bash
$ docker tag python-app:0.1 USERNAME/python-app:0.1

```

6. Open a session on Docker Hub and **push** your image:

 ```bash
$ docker login
$ docker push  USERNAME/python-app:0.1
 ```



7. Open Docker Hub web interface and **check** if the image was properly uploaded:

 https://hub.docker.com/



8. Ask one of your colleagues for his/her repository name and **deploy** a new container on your host:

 ```bash
$ docker run -d -p 5000 --name nginx-app COLLEAGUE/nginx-app:0.1


 ```

9. **Check** if the container is running:

 ```bash
$ docker ps


 ```

10. Check if the application is **reachable**:

```bash
$ curl localhost:5000
```



___





