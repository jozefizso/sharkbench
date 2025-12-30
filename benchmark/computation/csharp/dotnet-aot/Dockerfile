FROM mcr.microsoft.com/dotnet/sdk:10.0-aot AS build

WORKDIR /source

COPY --link . ./

RUN dotnet publish -c Release -o /app \
        && rm /app/*.dbg

FROM mcr.microsoft.com/dotnet/runtime-deps:10.0-noble-chiseled AS deploy

WORKDIR /app
COPY --link --from=build /app .

EXPOSE 3000
ENTRYPOINT ["./program"]
