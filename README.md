# dot-net-web-api

## Commands

```bash
dotnet new webapi -controllers -f net8.0
dotnet build
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

## Testing APIs with .http Files

.http files provide a standard format for testing API endpoints directly from your IDE. Supported in Visual Studio and Visual Studio Code (with REST Client extension).

The project includes `dot-net-web-api.http` file preconfigured with:

- `@dot_net_web_api_HostAddress` variables
- GET commands for testing endpoints
- Accepts `application/json` responses

1. Open the `.http` file
2. Click "Send Request" above any HTTP command
3. View the response in a new window

Example response:

```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "date": "2024-01-18",
        "temperatureC": -2,
        "temperatureF": 29,
        "summary": "Warm"
    },
    ...
]
```
