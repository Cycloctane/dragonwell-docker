FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:cd89230605f64f583a0beabceed19d50cb47d15f08657081a524a0afed1811fa\
    "https://github.com/dragonwell-project/dragonwell11/releases/download/\
dragonwell-standard-11.0.24.20_jdk-11.0.24-ga/Alibaba_Dragonwell_Standard_11.0.24.20.8_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]