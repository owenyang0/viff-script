FROM ubuntu:14.04

MAINTAINER Owen Yang <usay@outlook.com>

RUN apt-get update
RUN apt-get install -y build-essential python2.7 curl git
RUN git clone https://github.com/creationix/nvm.git /root/.nvm

RUN /bin/bash -c "source /root/.nvm/nvm.sh && nvm install 0.11 && \
    echo \"[[ -s /root/.nvm/nvm.sh ]] && . /root/.nvm/nvm.sh\" >> /root/.bashrc && \
    nvm alias default 0.11 && \
    ln -s /root/.nvm/v0.11.16/bin/npm /usr/local/bin/npm && \
    ln -s /root/.nvm/v0.11.16/bin/node /usr/local/bin/node && \
    ln -s /usr/bin/python2.7 /usr/local/bin/python && \
    echo $PATH && python --version && node -v"

ENV PATH /root/.nvm/bin:$PATH


ADD ./viff-auth /srv/viff-auth

WORKDIR /srv/viff-auth
RUN /bin/bash -c "cd /srv/viff-auth && source /root/.bashrc && npm install"

CMD npm run dev

# Expose ports.
EXPOSE 9999
