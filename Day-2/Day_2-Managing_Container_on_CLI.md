![docker-logo-150x150.png](https://www.zencode.nl/wp-content/uploads/2015/05/docker-logo-150x150.png)

# Day 2 - LAB - Managing Container on CLI



 1. Deploy a **new** container in **detached** mode using REDIS official image from DockerHub Registry, and name it as **redis**:
```bash 
      $ docker run -d --name redis redis
```

2. Check** if the container is running on Docker and the process running on Linux:

```bash 
    $ docker ps
    $ ps -ef | grep redis
```

3. Get a **prompt** on **redis** container and add some entries using *redis-cli*:
```bash 
	$ docker exec -it redis bash
	
	root@4ed58e3b64f3:/# redis-cli
	>  set docker great
	> set nutanix rocks
	> get docker
	> get nutanix
	> exit
```

4. **Create** a test file in the container's root directory and close the terminal returning to host:

```bash 
	root@4ed58e3b64f3:/ date > /datetime.txt
	root@4ed58e3b64f3:/ exit
```

5. **Check** if the entries previously added were stored by Redis:
```bash 
	$ docker exec redis sh -c "redis-cli --scan"
```

6. **Stop** the container and try to run container again:
```bash 
	$ docker stop redis
	$ docker run -d --name redis redis
```

7. **Start** REDIS and check if the information is preserved:
```bash 
	$ docker start redis
	$ docker exec redis sh -c "redis-cli --scan"
	$ docker exec redis ls /
```

8. Try  to **remove** 'redis' container:
```bash 
	$ docker rm redis
```
> **What happened?**

> **Option 1:** Stop the container and try the removal again
```bash 
	$ docker stop redis
	$ docker rm redis
```
>**Option 2:** Force a removal
```bash 
	$ docker rm -f redis
```



___





