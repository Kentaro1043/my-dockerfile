FROM httpd:2

RUN apt-get update && apt-get install --no-install-recommends -y  \
	git=1:2.39.2-1.1 \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/* \
    && rm -rf /usr/local/apache2/htdocs \
	&& git clone https://github.com/cpprefjp/cpprefjp.github.io /usr/local/apache2/htdocs
