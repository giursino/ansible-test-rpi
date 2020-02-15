# Docker image to test it

From [here](https://hub.docker.com/r/danielguerra/alpine-sshdhttps://hub.docker.com/r/danielguerra/alpine-sshd)

1) Create docker image:

    docker build -t myalpine .

2) Setup conintainer

    tar cv --files-from /dev/null | docker import - scratch
    docker create -v /root/.ssh --name ssh-container scratch /bin/true
    docker cp id_rsa.pub ssh-container:/root/.ssh/authorized_keys
    <change chown of authorized_key to root!!!!>

4) Start container

    docker run -p 4848:22 --name myalpine --hostname myalpine --volumes-from ssh-container --rm myalpine

5) Test SSH connection

   ssh -p 4848 root@localhost

6) Stop container

   docker stop myalpine

    
