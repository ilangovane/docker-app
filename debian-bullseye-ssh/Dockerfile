FROM debian:11

ENV LANG=fr_FR.UTF-8

RUN echo 'Acquire::https {  Verify-Peer "false"; Verify-Host "false"; }' > /etc/apt/apt.conf.d/ignore_ssl
 
RUN apt update && \
    apt install -y dos2unix curl wget vim nano openssh-server openssh-client ca-certificates locales git default-jdk libcap2-bin

RUN mkdir -p /run/sshd

RUN echo 'root:toor' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \ 
    sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config



EXPOSE 22
 
CMD [ "/usr/sbin/sshd" , "-D" ]




