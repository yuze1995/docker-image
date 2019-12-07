FROM jenkinsci/blueocean:latest

USER root

RUN wget https://download.visualstudio.microsoft.com/download/pr/c72122bd-38f5-4c98-b585-b8aaf57ecc6e/c89d7774a430e163d801753654f33972/dotnet-sdk-2.2.207-linux-musl-x64.tar.gz
RUN mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-2.2.207-linux-musl-x64.tar.gz -C $HOME/dotnet
ENV DOTNET_ROOT=/root/dotnet
ENV PATH=$PATH:/root/dotnet