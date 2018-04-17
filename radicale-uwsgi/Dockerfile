FROM alpine:3.7
EXPOSE 3031
WORKDIR /usr/src/app
COPY . .
RUN apk add --no-cache \
        python3 \
        uwsgi-python3 \
        py3-bcrypt \
        py3-cffi
RUN pip3 install --no-cache-dir -r requirements.txt
RUN mkdir /usr/src/app/data /usr/src/app/users
RUN chown uwsgi -R .
ENV RADICALE_CONFIG /usr/src/app/config.ini
CMD [ "uwsgi", "--ini", "uwsgi.ini", "--wsgi-file", "radicale.wsgi" ]
