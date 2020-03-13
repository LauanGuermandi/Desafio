FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# Copia o csproj e restaura as layers
COPY *.sln .
COPY Desafio-API/*.csproj ./aspnetapp/
RUN dotnet restore

# Copia o resto dos arquivos e faz a build
COPY Desafio-API/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app --no-restore

# Sobe o servidor
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1

# Faz da pasta 'app' o diretório atual de trabalho
WORKDIR /app

# Copia arquivos e pastas para o diretório atual de trabalho (pasta 'app')
COPY --from=build /app ./

ENTRYPOINT ["dotnet", "aspnetapp.dll"]