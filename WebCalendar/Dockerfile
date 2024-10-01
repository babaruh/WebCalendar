# Building

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app

COPY . .

WORKDIR /app/src/WebCalendar
RUN dotnet publish -c Release -o build

# Running

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS final-env
WORKDIR /app

COPY --from=build-env /app/src/WebCalendar/build .

RUN dotnet dev-certs https
EXPOSE 5099
ENTRYPOINT ["dotnet", "WebCalendar.dll"]
