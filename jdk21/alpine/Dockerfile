# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:0b38d2bb820708cf16cd606563b345eec385c20d535c8e5d2d7050ed2b00ea17\
    "https://github.com/dragonwell-project/dragonwell21/releases/download/\
dragonwell-standard-21.0.4.0.4%2B7_jdk-21.0.4-ga/Alibaba_Dragonwell_Standard_21.0.4.0.4.7_x64_alpine-linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM alpine:3.20

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]