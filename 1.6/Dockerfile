FROM balenalib/rpi-raspbian:jessie

RUN [ "cross-build-start" ]

MAINTAINER Tobias Hargesheimer <docker@ison.ws>

ENV NGINX_VERSION 1.6.*

RUN apt-get update \
	&& apt-get install -y ca-certificates nginx=${NGINX_VERSION} \
	&& rm -rf /var/lib/apt/lists/*

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

RUN [ "cross-build-end" ]
	
EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
