## DGX Support


#### Troubleshooting
If `nvidia-docker ps -a` does not respond,
```
admin@server:~$ sudo service docker restart
admin@server:~$ sudo docker ps - -all
```
the docker daemon service might be dead.

#### To check DGX device status

To display DGX topology:
```
nvidia-smi topo -m
```

To query device:
```
/usr/local/cuda/samples/1_Utilities/deviceQuery/deviceQuery
```



#### Nova Global IT support

To raise tickets for any DGX related problems:
- [NVIDIA Support Portal](https://nvidia-esp.custhelp.com/)

IT support for DGX-1(send to both):
- [M Teguh Satria](mailto:teguh@novaglobal.com.sg)
- [Support](mailto:support@novaglobal.com.sg)
