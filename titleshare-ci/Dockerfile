FROM debian:stretch-slim

ENV LANG="C.UTF-8"

RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        python3 \
        python3-dev \
        python3-pip \
        python3-setuptools \
        curl \
        gnupg \
        && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN pip3 install awsebcli --upgrade --user  
ENV PATH=~/.local/bin:$PATH

RUN curl -sL https://deb.nodesource.com/setup_11.x | bash -
RUN apt-get install -y nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

RUN VER="17.03.0-ce" \
       && curl -L -o /tmp/docker-$VER.tgz https://download.docker.com/linux/static/stable/x86_64/docker-$VER.tgz \
       && tar -xz -C /tmp -f /tmp/docker-$VER.tgz \
       && mv /tmp/docker/* /usr/bin


