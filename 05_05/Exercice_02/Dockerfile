FROM alpine:3.17
COPY hello.c /
RUN apk add gcc libc-dev \
 && gcc -o hello hello.c
CMD ["/hello"]
