docker build -t 127.0.0.1/test/test - << EOF
FROM ubuntu
RUN echo world > /hello
EOF




$ docker push  127.0.0.1/test/test