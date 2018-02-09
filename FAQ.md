## Frequently Asked Questions

1. Can I `sudo apt-get`?

You are allowed to `sudo apt-get` if you are within your **own** container. Please
do not use the `sudo` command outside of your **own** container.

2. I can't find my container? Did someone remove it?

Please be advised that when launching your container from an image the first
time, please name your container, e.g. `user_pycuda` so you are able to find
your containers easily using the `nvidia-docker ps -a | grep user`.
