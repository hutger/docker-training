![docker-logo-150x150.png](https://www.zencode.nl/wp-content/uploads/2015/05/docker-logo-150x150.png)

# Day 4 - LAB - Volumes



**Objetives:**

- Create a named volume for storing MariaDB data files;
- Run a MariaDB container, mounting a named volume store;
- Create a secondary named volume for storing MariaDB backups;
- Run a transitory container for backing up MariaDB (by copying the datafiles and using mysqldump)

 

___



1. **Create a volume** called 'mariadb-vol':

 ```bash
$ docker volume create mariadb-vol

 ```

2. **Start an new container** with volume *mariadb-vol* attached

 ```bash
$ docker run --name my-mariadb -p 3306:3306 -v mariadb-vol:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=nutanix -d mariadb:10

 ```

3. **Check database** connectivity:

```bash
$ nc -v localhost 3306
```



4. **Compare** the contents from container and host:

```bash
$ docker exec -it my-mariadb bash -c "ls /var/lib/mysql"

$ ls -la /var/lib/docker/volumes/mariadb-vol/_data
```



5. **Spin up another container** mounting *mariadb_vol* in order to check the content:

```bash
$ docker run --rm --name mariadb-backup \
-v mariadb-vol:/backup \
-it ubuntu \
bash -c "ls -la /backup"
```



6. Create a **second named volume** called *mariadb-backup*:

```bash
$ docker volume create mariadb-backup
```



7. Run a transitory container in order to **backup mariadb datafiles**:

```bash
$ docker run --name mariadb-backup --rm \
-v mariadb-vol:/mariadb-data \
-v mariadb-backup:/backup \
-it ubuntu bash \
-c "tar -cjvf /backup/maria_backup.tar.bz2 /mariadb-data"
```



8. **Check the backup** file created on the host:

```bash
$ ls -la /var/lib/docker/volumes/mariadb-backup/_data 

```

9. Another option (and recommended), is to perform the **backup using mysqldump**:

 ```bash
$ docker run --name mariadb-backup --rm \
-v mariadb-vol:/mariadb-data \
-v mariadb-backup:/backup \
--link my-mariadb \
-it mariadb:10 
bash -c "mysqldump -h my-mariadb --all-databases -u root -pnutanix > /backup/maria_backup.tar.bz2"
 ```



___

