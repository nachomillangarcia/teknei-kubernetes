FROM ubuntu

RUN cd /app && \
  apt update \
  && apt install -y nginx \
  && cd /app \
  && ls 

WORKDIR /root

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]