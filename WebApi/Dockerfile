FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app
COPY WebApi.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o out
EXPOSE 5001

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS RUNTIME
WORKDIR /app
COPY --from=build /app/out ./out
ENV ASPNETCORE_URLS=http://*:5001
EXPOSE 5001
CMD ["dotnet", "out/WebApi.dll"]
