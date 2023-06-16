FROM debian:bullseye-slim

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV SHELL /bin/bash

# パッケージをインストール
RUN apt-get update && apt-get install -y --no-install-recommends \
	python3-pip \
	build-essential \
	gdb \
	time \
	curl \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

# atcoderユーザー作成
RUN groupadd atcoder \
	&& useradd -m -g atcoder atcoder \
	&& echo "atcoder ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# workspace作成
RUN mkdir -p /home/atcoder/workspace \
	&& chown -R atcoder:atcoder /home/atcoder/workspace

# ユーザー切り替え
USER atcoder

# ワークスペース切り替え
WORKDIR /home/atcoder/workspace

# 設定ディレクトリ作成
RUN mkdir -p /home/atcoder/.config/atcoder-cli-nodejs \
	&& chown -R atcoder:atcoder /home/atcoder/.config/atcoder-cli-nodejs \
	&& mkdir -p /home/atcoder/.local/share/online-judge-tools \
	&& chown -R atcoder:atcoder /home/atcoder/.local/share/online-judge-tools

# nvmをインストール
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash \
	&& source ~/.nvm/nvm.sh \
	&& nvm install --lts \
	&& npm install -g atcoder-cli

# online-judge-toolsをインストール
RUN pip install --no-cache-dir online-judge-tools \
	&& echo 'export PATH="/home/atcoder/.local/bin:$PATH"' >> ~/.bashrc

VOLUME [ "/home/atcoder/workspace", "/home/atcoder/.config/atcoder-cli-nodejs", "/home/atcoder/.local/share/online-judge-tools" ]
