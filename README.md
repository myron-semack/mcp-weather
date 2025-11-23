# MCP Weather Server (AccuWeather)

A simple MCP server that provides hourly weather forecasts using the AccuWeather API.

Forked from [adhikasp/mcp-weather](https://github.com/adhikasp/mcp-weather) for personal development.

## Setup

1. Install dependencies using `uv`:
```bash
uv venv
uv sync
```

2. Create a `.env` file with your AccuWeather API key:
```
ACCUWEATHER_API_KEY=your_api_key_here
```

You can get an API key by registering at [AccuWeather API](https://developer.accuweather.com/).

## Running the Server

```json
{
    "mcpServers": {
        "weather": {
            "command": "uvx",
            "args": ["--from", "git+https://github.com/myron-semack/mcp-weather.git", "mcp-weather"],
            "env": {
                "ACCUWEATHER_API_KEY": "your_api_key_here"
            }
        }
    }
}
```

## API Usage

### Get Hourly Weather Forecast

Response:
```json
{
  "location": "State College",
  "location_key": "335315",
  "country": "United States",
  "current_conditions": {
    "temperature": {
      "value": 6.9,
      "unit": "C"
    },
    "weather_text": "Mostly clear",
    "relative_humidity": null,
    "precipitation": false,
    "observation_time": "2025-11-23T18:32:00-05:00"
  },
  "hourly_forecast": [
    {
      "relative_time": "+1 hour",
      "temperature": {
        "value": 6.7,
        "unit": "C"
      },
      "weather_text": "Partly cloudy",
      "precipitation_probability": 0,
      "precipitation_type": null,
      "precipitation_intensity": null
    }
  ]
}
```

The API provides:
- Current weather conditions including temperature, weather description, humidity, and precipitation status
- 12-hour forecast with hourly data including:
  - Relative time from current time
  - Temperature in Celsius
  - Weather description
  - Precipitation probability, type, and intensity