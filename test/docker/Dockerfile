FROM python:alpine
MAINTAINER Giuseppe Ursino <giursino@gmail.com>

# add openssh and clean
RUN apk add --update openssh \
&& rm  -rf /tmp/* /var/cache/apk/*
# add entrypoint script
ADD docker-entrypoint.sh /usr/local/bin
#make sure we get fresh keys
RUN rm -rf /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_dsa_key
# Generate keys
#RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''
# Unlock root account
RUN passwd -u root
#RUN docker-entrypoint.sh

EXPOSE 22
ENTRYPOINT ["docker-entrypoint.sh"]
#ENTRYPOINT ["/bin/sh"]
CMD ["/usr/sbin/sshd","-D"]
