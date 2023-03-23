FROM alpine:3.17 AS first
COPY hello.c /
RUN apk add gcc libc-dev \
 && gcc -o hello hello.c
FROM alpine:3.17 AS second
COPY --from=first hello /
CMD ["/hello"]
