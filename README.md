# dot-net-web-api

An ASP.NET Core web API running on .NET 8.0 that demonstrates CRUD operations (Create, Read, Update, Delete) for managing pizzas using an in-memory cache.

## Overview

This project demonstrates creating a web API with ASP.NET Core by:

- Creating a new application using the ASP.NET Core Web API template
- Creating controller classes that inherit from `ControllerBase` with methods that respond to HTTP requests
- Focusing on individual controller actions to build functional web APIs quickly

**Note:** This implementation uses an in-memory cache for simplicity and CRUD demonstration purposes. Data is not persisted and will be lost when the application stops. Production applications should use a database or persistent storage.

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

# Get a specific item by ID
get 1

# Exit HttpRepl
exit
```

### Testing CRUD Operations with HTTP REPL

Navigate to an endpoint and list operations:

```bash
cd Pizza
ls
# Output shows: .  [GET|POST]  and  {id}  [GET|PUT|DELETE]
```

**CREATE** - Add a new item with POST:

```bash
post -c "{"name":"Hawaii", "isGlutenFree":false}"
# Returns 201 Created with the new item
```

**UPDATE** - Modify an item with PUT:

```bash
put 3 -c "{"id": 3, "name":"Hawaiian", "isGlutenFree":false}"
# Returns 204 No Content on success
```

**READ** - Get items:

```bash
# Get all items
get

# Get specific item by ID
get 3
# Returns 200 OK with the item
```

**DELETE** - Remove an item:

```bash
delete 3
# Returns 204 No Content on success
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
