FROM mcr.microsoft.com/dotnet/core/sdk:3.0

# Install OpenJDK
RUN apt-get update \
    && apt-get install -y openjdk-11-jdk

# Install sonar sacanner .net core 3.0 version to dotnet tool
ENV SONAR_SCANNER_NUGET_TOOL_VERSION=4.8.0

RUN dotnet tool install --global dotnet-sonarscanner --version $SONAR_SCANNER_NUGET_TOOL_VERSION 
ENV PATH="$PATH:/root/.dotnet/tools"

# Cleanup
RUN apt-get -q autoremove \
    && apt-get -q clean -y \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*.bin