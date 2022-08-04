FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
EXPOSE 80
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src

# note: build context is the repo root directory
COPY . .

RUN dotnet publish ./DotnetDockerDebugRepro/DotnetDockerDebugRepro.csproj -o /app


FROM base as final

COPY --from=build /app .
ENTRYPOINT [ "/usr/bin/dotnet", "/app/DotnetDockerDebugRepro.dll" ]
