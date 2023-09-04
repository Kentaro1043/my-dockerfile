FROM codercom/code-server:latest

USER root

RUN apt-get update && \
    apt-get install -y openjdk-17-jdk

USER coder

RUN mkdir -p /home/coder/.config/code-server && \
    mkdir -p /home/coder/project

ADD --chown=coder:coder redhat.java.vsix .

RUN code-server --install-extension redhat.java.vsix \
    && rm redhat.java.vsix

WORKDIR /home/coder/project
