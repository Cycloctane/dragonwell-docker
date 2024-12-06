# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:bd5c08ae46976663f12c82ec0c86bf2dae7aa1ee1ae26defe86ef8c06a1f43bd\
    "https://github.com/dragonwell-project/dragonwell11/releases/download/\
dragonwell-standard-11.0.25.21_jdk-11.0.25-ga/Alibaba_Dragonwell_Standard_11.0.25.21.9_x64_alpine-linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM alpine:3.20

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]