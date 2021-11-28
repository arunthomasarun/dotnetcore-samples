FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as Build
WORKDIR /source
COPY . .
RUN dotnet restore
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /publishedapp

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 as Package
EXPOSE 80
WORKDIR /app
COPY --from=Build /publishedapp .
ENV ASPNETCORE_URLS http://*:80
CMD dotnet aspnetapp.dll