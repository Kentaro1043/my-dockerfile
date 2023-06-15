FROM codercom/code-server:latest

USER root

RUN apt-get update && \
    apt-get install -y openjdk-17-jdk

USER coder

RUN mkdir -p /home/coder/.config/code-server && \
    mkdir -p /home/coder/project

ADD --chown=coder:coder redhat.java-1.18.0.vsix .

RUN code-server --install-extension redhat.java-1.18.0.vsix \
    && rm redhat.java-1.18.0.vsix

WORKDIR /home/coder/project
