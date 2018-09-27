#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see https://aka.ms/containercompat

FROM microsoft/dotnet:2.1-aspnetcore-runtime-nanoserver-sac2016 AS base
WORKDIR /app
EXPOSE 57446
EXPOSE 44350

FROM microsoft/dotnet:2.1-sdk-nanoserver-sac2016 AS build
WORKDIR /src
COPY ["ds-core-website/ds-core-website.csproj", "ds-core-website/"]
RUN dotnet restore "ds-core-website/ds-core-website.csproj"
COPY . .
WORKDIR "/src/ds-core-website"
RUN dotnet build "ds-core-website.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "ds-core-website.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "ds-core-website.dll"]