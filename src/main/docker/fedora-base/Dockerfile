FROM fedora:latest

# Expose SSH
EXPOSE 22

# install minimum requirements for ansible
RUN /usr/bin/dnf -y update & /usr/bin/dnf install -y openssh-server python
RUN /usr/bin/ssh-keygen -A
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

# copy ssh key
RUN mkdir /root/.ssh
COPY id_rsa.pub /root/.ssh/authorized_keys

CMD ["/usr/sbin/sshd", "-D"]
