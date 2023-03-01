FROM alpine:latest

ENV PATH=/usr/local/bin:$PATH LANG=C.UTF-8

EXPOSE 80

WORKDIR /app/

COPY ./official/* /app/
RUN java -Djava.library.path=prebuilt/linux64 
RUN set -ex \
&& apk update -f \
&& apk upgrade \
&& apk add openjdk11 busybox unzip \
&& ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
&& echo "Asia/Shanghai" > /etc/timezone \
&& rm -rf /var/cache/apk/* \
&& mv /app/*.sh /usr/local/bin \
&& chmod +x /usr/local/bin/*.sh

ENTRYPOINT ["entrypoint.sh"]
