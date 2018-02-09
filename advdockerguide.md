## Advanced Guide to using `nvidia-docker`

#### How to scp files from DGX to local
```
$ scp username@server:/home/username/directory/you/want /local/directory/you/want/filename
```

#### How to scp files from local to DGX
```
$ scp /local/directory/you/want/filename username@server:/home/username/directory/you/want
```
Note: for folders, use `-r` handle.

#### To save your docker image
```
username@server:~$ nvidia-docker commit *DOCKERNAMETOCOMMIT* *IMAGENAMETOSAVEAS*
```


#### To transfer from host to docker container
```
username@server:~$ nvidia-docker cp *./nameoffile* *dockername/number*:/*dockerdirectory*
username@server:~$ nvidia-docker cp ./README.md my_pyconda3:/
username@server:~$ nvidia-docker cp ./README.md e74d0:/
```
the first 5 characters of the container ID is sufficient to identify the container.


#### To transfer from docker container to host
```
username@server:~$ nvidia-docker cp *dockername/number*:/*dockerdirectorywithfile* *./*
username@server:~$ nvidia-docker cp my_pyconda3:/README.md ./
username@server:~$ nvidia-docker cp e74d0:/README.md ./
```


#### Installation of pycuda
Install `Anaconda3`, install `pip` and upgrade it, then `pip install pycuda`.
