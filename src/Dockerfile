FROM mcr.microsoft.com/dotnet/sdk:5.0-alpine AS build
WORKDIR /src

COPY BlazorK8s/*.csproj ./BlazorK8s/
RUN dotnet restore ./BlazorK8s/*.csproj

COPY BlazorK8s/. ./BlazorK8s/
WORKDIR /src/BlazorK8s
RUN dotnet publish -c release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:5.0-alpine
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "BlazorK8s.dll"]