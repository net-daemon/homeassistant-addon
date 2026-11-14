# NetDaemon V7 - alpha (.NET 11)

This is the manually published alpha version of NetDaemon V7, built on .NET 11.
It uses `ghcr.io/net-daemon/netdaemon_addon7:alpha` and supports aarch64 and amd64.

The V7 alpha is a separate add-on with the slug `netdaemon7-alpha`. Its default application folder is `/config/netdaemon7`. Existing V6 and older add-ons remain separate.

Update your application packages to the matching V7 alpha versions. For compiled applications, target `net11.0`, rebuild with the .NET 11 SDK, and deploy the complete build output. Source deployments continue to use `.cs` files; `.csproj` deployment is not supported.

Alpha releases can change between builds. Use the stable add-on for production automations.
