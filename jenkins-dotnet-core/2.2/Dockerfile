FROM jenkinsci/blueocean:latest

USER root

# Install Dotnet Core 2.2 Runtime Dependencies
# reference https://github.com/dotnet/dotnet-docker/blob/44244f08d71f509c735738da10a94d03374b3c5a/2.1/runtime-deps/alpine3.9/amd64/Dockerfile
RUN apk add --no-cache \
        ca-certificates \
        # .NET Core dependencies
        krb5-libs \
        libgcc \
        libintl \
        libssl1.1 \
        libstdc++ \
        lttng-ust \
        tzdata \
        userspace-rcu \
        zlib

# Install Dotnet Core 2.2 SDK Dependencies  
# reference https://github.com/dotnet/dotnet-docker/blob/5c25dd2ed863dfd73edb1a6381dd9635734d0e5f/2.2/sdk/alpine3.9/amd64/Dockerfile
RUN apk add --no-cache icu-libs

# Install Dotnet Core 2.2 SDK
RUN wget https://download.visualstudio.microsoft.com/download/pr/c72122bd-38f5-4c98-b585-b8aaf57ecc6e/c89d7774a430e163d801753654f33972/dotnet-sdk-2.2.207-linux-musl-x64.tar.gz
RUN mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-2.2.207-linux-musl-x64.tar.gz -C $HOME/dotnet
ENV DOTNET_ROOT=/root/dotnet
ENV PATH=$PATH:/root/dotnet

RUN rm -rf dotnet-sdk-2.2.207-linux-musl-x64.tar.gz