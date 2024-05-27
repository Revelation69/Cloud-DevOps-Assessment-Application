# Stage 1: Build the application
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /source

# Copy the project file and restore dependencies
COPY aspnet-core-dotnet-core/aspnet-core-dotnet-core.csproj .
RUN dotnet restore aspnet-core-dotnet-core.csproj

# Copy the rest of the source code and build the application
COPY aspnet-core-dotnet-core/. .
RUN dotnet publish aspnet-core-dotnet-core.csproj -c Release -o /app

# Stage 2: Create the runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim
WORKDIR /app

# Copy the build output from the build stage
COPY --from=build /app .

# Run the application
ENTRYPOINT ["dotnet", "aspnet-core-dotnet-core.dll"]

