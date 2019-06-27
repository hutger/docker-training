![docker-logo-150x150.png](https://www.zencode.nl/wp-content/uploads/2015/05/docker-logo-150x150.png)





# Day 1 - LAB - Docker Installation



**Objetives:**

- Install Docker using convenience script
- Enabling an starting Docker
- Check version

 

___





1. **Install Docker** using convenience script

```bash
$ curl -fsSL https://get.docker.com/ | sh
```



2. **Enable** Docker on startup and **start** the service: 

```bash
$ systemctl enable docker
$ systemctl start docker
```



3. **Check** the Docker **version** installed:

 ```bash
$ Docker --version
Docker version 18.09.6, build 481bc77

 ```

___

