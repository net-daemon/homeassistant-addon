# NetDaemon V7 (.NET 11)

NetDaemon runs C# home automations for Home Assistant. V7 uses .NET 11 and supports aarch64 and amd64.

V7 is a separate add-on with the slug `netdaemon7`. Its default application folder is `/config/netdaemon7`. V6 and older add-ons remain available separately.

## Applications

Use the matching NetDaemon V7 NuGet packages. Compiled applications must target `net11.0` and be rebuilt with the .NET 11 SDK. Deploy the complete build output and select the application DLL in the add-on configuration. Source deployments use `.cs` files; `.csproj` deployment is not supported.

## Documentation

- [Development environment](https://netdaemon.xyz/docs/user/started/development)
- [NetDaemon releases](https://github.com/net-daemon/netdaemon/releases)
- [User documentation](https://netdaemon.xyz)
