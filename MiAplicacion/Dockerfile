# Usa una imagen base de .NET SDK para compilar la aplicación
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app

# Copia los archivos del proyecto al contenedor
COPY . .

# Restaura las dependencias y compila la aplicación
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Usa una imagen base de .NET Runtime para ejecutar la aplicación
FROM mcr.microsoft.com/dotnet/runtime:7.0
WORKDIR /app
COPY --from=build /app/out .

# Comando para ejecutar la aplicación
ENTRYPOINT ["dotnet", "MiAplicacion.dll"]
