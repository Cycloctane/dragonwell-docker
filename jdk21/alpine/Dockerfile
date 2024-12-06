# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:c9c4746f89a3d5d55a96ee02f4286c1fe8ce0f5d7b6a12e885b87be613141ddd\
    "https://github.com/dragonwell-project/dragonwell21/releases/download/\
dragonwell-standard-21.0.5.0.5%2B9_jdk-21.0.5-ga/Alibaba_Dragonwell_Standard_21.0.5.0.5.9_x64_alpine-linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM alpine:3.20

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]