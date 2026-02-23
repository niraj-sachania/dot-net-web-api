# dot-net-web-api

## Commands

```bash
dotnet new webapi -controllers -f net8.0
dotnet run
```

## Exploring APIs with HTTP REPL

Install the .NET HTTP REPL tool:

```bash
dotnet tool install -g Microsoft.dotnet-httprepl
```

Connect to the web API:

```bash
httprepl https://localhost:{PORT}
# or after HttpRepl is running:
connect https://localhost:{PORT}
```

Navigate and test endpoints:

```bash
# List available endpoints
ls

# Navigate to an endpoint
cd WeatherForecast

# Make a GET request
get

# Exit HttpRepl
exit
```
