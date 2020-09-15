# Use existing image as base
FROM mcr.microsoft.com/dotnet/core/sdk
WORKDIR /tmp/app

# Install dependencies
RUN dotnet tool install --global dotnet-sonarscanner --version 4.10.0
COPY . .
RUN dotnet add consoleproject package Microsoft.NET.Test.Sdk --version 16.7.1
RUN dotnet add consoleproject package dotnet-xunit --version 2.3.1
RUN dotnet build consoleproject/consoleproject.csproj /p:StartupObject=consoleproject.Program

## AFTER EACH COMMAND A SNAPSHOT OF TEMP CONTAINER IS SAVED (TEMP IMAGE) ##
## THE NEXT COMMAND PICKS UP THAT TEMP IMAGE, RUNS A NEW TEMP CONTAINER, EXECUTES COMMAND, STOPS and so on ##

# Tell the image what to do when it starts as a container
CMD ["dotnet", "run", "--project", "consoleproject/consoleproject.csproj"]