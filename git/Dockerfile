FROM debian:latest

RUN apt-get update && \
    apt-get install -y openssh-server git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/run/sshd

ENV GIT_HOME /home/git

ARG user=git
ARG group=git
ARG uid=1000
ARG gid=1000

RUN groupadd -g ${gid} ${group} \
    && useradd -d "$GIT_HOME" -u ${uid} -g ${gid} -m -s /usr/bin/git-shell ${user}

RUN echo 'git:password' | chpasswd

RUN mkdir -p /repos

VOLUME /repos/

EXPOSE 22

ENTRYPOINT ["/usr/sbin/sshd", "-D"]
