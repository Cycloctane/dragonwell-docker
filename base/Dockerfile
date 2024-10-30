ARG BASE_IMAGE
FROM alpine:3.20

WORKDIR /tmp

ARG DOWNLOAD_URL
ADD ${DOWNLOAD_URL} ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip || rm openjdk/src.zip

FROM ${BASE_IMAGE}

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"

# java 8:
# CMD [ "sh" ]

# java 9+:
CMD [ "jshell" ]