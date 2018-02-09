## Guide to using `nvidia-docker`

Note that if you choose to use `docker` commands instead of `nvidia-docker`,
your work might not be running on the GPU.

#### To check your cuda version,
```
username@server:~$ nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Sun_Sep__4_22:14:01_CDT_2016
Cuda compilation tools, release 8.0, V8.0.44
```

#### To check what images you have,
```
username@server:~$ nvidia-docker images
```

#### To run a docker image,
```
username@server:~$ nvidia-docker run -it --name *NAMEFORYOURDOCKER* *IMAGEID*
```

Note: In the naming of your docker, you might like to prefix the name with your initials e.g. `my_pyconda3` so you can find your containers much easily,

```
username@server:~$ nvidia-docker ps -a | grep my
username@server:~$ nvidia-docker ps -a | grep my
616ae2c5df7b        pycuda                            "/bin/bash"              5 minutes ago       Exited (0) 7 seconds ago                        my_pycuda
```

To get some basic stuff, like `pip` and `curl`,
```
username@server:~$ sudo apt-get install python-pip python-dev build-essential
username@server:~$ sudo pip install --upgrade pip
```

----

### Anaconda3

To use Anaconda3, there is a image named `pyconda3`. You can run a container with this image,
```
username@server:~$ nvidia-docker run -it --name my_pyconda3 pyconda3
```
In the command above, `my_pyconda3` is the name that is assigned to your container(please use another name when you try) and `pyconda3` is the name of the image you are using for your container. You will then get something like below,
```
root@d8bf528b7a96:/#
```
which means you are in your new container. You can check which `Python3` distribution you are currently on now,
```
root@d8bf528b7a96:~# which python
/usr/bin/python
```
which is not the `Anaconda3` distribution. `Anaconda3` is located at `/root/anaconda3` and to activate it, simply
```
root@d8bf528b7a96:/# cd /root/anaconda3
root@d8bf528b7a96:~/anaconda3# source bin/activate ~/anaconda3/
(/root/anaconda3/) root@d8bf528b7a96:~/anaconda3#
```
You are using `Anaconda3` now, which can be easily checked with
```
(/root/anaconda3/) root@d8bf528b7a96:~/anaconda3# which python
/root/anaconda3/bin/python
```
To create specialized conda environments, refer to the [conda documentation](https://conda.io/docs/using/envs.html)

To exit the `Anaconda3` environment, simply
```
(/root/anaconda3/) root@d8bf528b7a96:~/anaconda3# source deactivate
root@d8bf528b7a96:~/anaconda3#
```

To exit you container without exiting the shell so your processes in your container
are still running, use the escape sequence
<kbd>Ctrl</kbd> + <kbd>p</kbd>, <kbd>Ctrl</kbd> + <kbd>q</kbd>  
will help you turn interactive mode into daemon mode

To exit your container,
```
root@d8bf528b7a96:~/anaconda3# exit
username@server:~$
```

If you want to re-enter the container,
```
nvidia-docker restart my_pyconda3
nvidia-docker attach my_pyconda3
```
`restart` is to get the container to start running and `attach` is to enter the container.

If you are done with your container, meaning you do not need it anymore,
```
username@server:~$ nvidia-docker stop my_pyconda3
username@server:~$ nvidia-docker rm my_pyconda3
```
where `stop` will stop the container and `rm` will permanently delete your container. **Only do that your your containers only!**

#### Listing containers

To see the list of containers that are still running,
```
username@server:~$ nvidia-docker ps
```

To see the list of containers inhibiting the server,
```
username@server:~$ nvidia-docker ps --all
```

To see the list of containers inhibiting the server with a particular keyword,
```
username@server:~$ nvidia-docker ps -a | grep *keyword*
```

#### List of images

Refer to the list of images [here](https://github.com/sutddgxadmin/sutdcompute/blob/master/imagelist.md).
