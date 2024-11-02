# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:d1c359795d3867413549f7a9dfea0a5ae0f304ad82065c797646625c092c3c3d\
    "https://github.com/dragonwell-project/dragonwell17/releases/download/\
dragonwell-standard-17.0.11.0.12%2B9_jdk-17.0.11-ga/Alibaba_Dragonwell_Standard_17.0.11.0.12.9_x64_alpine-linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM alpine:3.20

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]