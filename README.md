# Lovelace animated weather card

Originally created for the [old UI](https://community.home-assistant.io/t/custom-ui-weather-state-card-with-a-question/23008) converted by @arsaboo and @ciotlosm to [Lovelace](https://community.home-assistant.io/t/custom-ui-weather-state-card-with-a-question/23008/291) and now converted to Lit to make it even better.

This card uses the awesome [animated SVG weather icons by amCharts](https://www.amcharts.com/free-animated-svg-weather-icons/).

![Weather Card](https://github.com/Warter21/weather-card/blob/master/weather-card.png?raw=true)

Thanks for all picking this card up.

## Installation:

### If you are using Firefox:

Firefox < 66 does not support all the needed functions yet for the editor.
You change this by enabling `javascript.options.dynamicImport` in `about:config`.
Or use the version without the editor: [Version without editor](https://raw.githubusercontent.com/bramkragten/custom-ui/58c41ad177b002e149497629a26ea10ccfeebcd0/weather-card/weather-card.js)

# Manual:

1. Download the [weather-card.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card.js) to `/config/www/custom-lovelace/weather-card/`. (or an other folder in `/config/www/`)
2. Save, the [amCharts icons](https://www.amcharts.com/free-animated-svg-weather-icons/) (The contents of the folder "animated") under `/config/www/custom-lovelace/weather-card/icons/` (or an other folder in `/config/www/`)
3. If you use Lovelace in storage mode, and want to use the editor, download the [weather-card-editor.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card-editor.js) to `/config/www/custom-lovelace/weather-card/`. (or the folder you used above)

Add the following to resources in your lovelace config:

```yaml
resources:
  - url: /local/custom-lovelace/weather-card/weather-card.js
    type: module
```

## Configuration:

And add a card with type `custom:weather-card`:

```yaml
type: custom:weather-card
entity: weather.openweathermap
name: Optional name
```

If you want to use your local icons add the location to the icons:

```yaml
type: custom:weather-card
entity: weather.openweathermap
icons: "/local/custom-lovelace/weather-card/icons/"
```

You can choose wich elements of the weather card you want to show:

The 3 different rows, being:

- The current weather icon, the current temperature and title
- The details about the current weather
- The X day forecast or hourly forecast

```yaml
type: custom:weather-card
entity: weather.openweathermap
current: true
details: false
forecast: true
hourly_forecast: false
number_of_forecasts: 5
```

### OpenWeather Map:

When using OpenWeather map you can select hourly(default) or daily forecast to show.

```yaml
# Example configuration.yaml entry
weather:
  - platform: openweathermap
    api_key: YOUR_API_KEY
```
