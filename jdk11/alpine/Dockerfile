# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:83da7d2ad15a6b88b2c540b784f968224f38c1ba07a9089c4de5de63ad80ff39\
    "https://github.com/dragonwell-project/dragonwell11/releases/download/\
dragonwell-standard-11.0.24.20_jdk-11.0.24-ga/Alibaba_Dragonwell_Standard_11.0.24.20.8_x64_alpine-linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM alpine:3.20

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]