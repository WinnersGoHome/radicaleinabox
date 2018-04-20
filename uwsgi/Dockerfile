FROM alpine:3.7
EXPOSE 3031
WORKDIR /usr/local/radicale
COPY . .
RUN apk add --no-cache \
        python3 \
        uwsgi-python3 \
        py3-bcrypt \
        py3-cffi && \
    pip3 install --no-cache-dir \
        radicale \
        passlib
RUN mkdir ./data && cp ./users.default ./data/users && chown uwsgi:uwsgi -R .
ENV RADICALE_CONFIG /usr/local/radicale/radicale.ini
VOLUME /usr/local/radicale/data
CMD [ "uwsgi", "--ini", "uwsgi.ini", "--wsgi-file", "radicale.wsgi" ]
