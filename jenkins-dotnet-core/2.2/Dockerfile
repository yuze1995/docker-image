FROM jenkinsci/blueocean:latest

USER root

# Install Dotnet Core 2.2 Runtime Dependencies
# reference https://github.com/dotnet/dotnet-docker/blob/5c25dd2ed863dfd73edb1a6381dd9635734d0e5f/2.2/sdk/alpine3.10/amd64/Dockerfile#L5
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
        zlib \
# Install Dotnet Core 2.2 SDK Dependencies  
# reference https://github.com/dotnet/dotnet-docker/blob/5c25dd2ed863dfd73edb1a6381dd9635734d0e5f/2.2/sdk/alpine3.9/amd64/Dockerfile
        icu-libs

# Install Dotnet Core 2.2 SDK
# reference https://github.com/dotnet/dotnet-docker/blob/5c25dd2ed863dfd73edb1a6381dd9635734d0e5f/2.2/sdk/alpine3.10/amd64/Dockerfile#L14
ENV DOTNET_SDK_VERSION 2.2.207
RUN wget -O dotnet.tar.gz https://dotnetcli.azureedge.net/dotnet/Sdk/$DOTNET_SDK_VERSION/dotnet-sdk-$DOTNET_SDK_VERSION-linux-musl-x64.tar.gz \
    && dotnet_sha512='231118ba205b5d609263fc790851c65900aabf5830d492425849de89b7103f02012a302ce21960cb062426c5b8fd480e1316176a927bd287b08b7d19445f7224' \
    && echo "$dotnet_sha512  dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -C /usr/share/dotnet -xzf dotnet.tar.gz \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet \
    && rm dotnet.tar.gz

# Install sonar sacanner .net core 3.0 version to dotnet tool
RUN dotnet tool install --global dotnet-sonarscanner --version 4.8.0
ENV PATH="$PATH:/root/.dotnet/tools"