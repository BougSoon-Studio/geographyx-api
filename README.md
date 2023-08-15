# What is GeographyX

GeographyX is a JavaScript API that enables you to retrieve detailed information about countries, access a complete list of world countries, retrieve country data based on information and obtain weather information for a country

## Installation

To integrate the Smart Development Kit into your application, follow this simple step:

1. Include the JavaScript library in the `<head>` of your HTML page:

```html
<script type="module">
    import * as GeographyX from "https://bgsn-files.web.app/geographyx/geographyx.js";
</script>
```

# Using GeographyX

## Get a free token

You can get a free token at: https://geographyx-api.web.app/get/token or use the free public token: `FREE_TOKEN`

## Available Functions

- `const MyToken = await GeographyX.Auth("YOUR_TOKEN");`: To use our API, you must have a token, which you can obtain for free at https://geographyx-api.web.app/get/token, or use the token: "FREE_TOKEN". Replace `YOUR_TOKEN` with your token.
- `const TokenToVerif = await GeographyX.VerifAuth("YOUR_TOKEN_YOU_WANT_VERIF");`: Use this line to verify a token. Replace `YOUR_TOKEN_YOU_WANT_VERIF` with a token.

- `GeographyX.getCountryInfo(country, field)`: Returns detailed information about the specified `country` along with the specific information requested with `field`.
- `GeographyX.getCountryInfo(country)`: Returns all information about the specified `country`.
- `GeographyX.getAllCountries(await GeographyX.fetchCountryData())`: Returns all countries.
- `GeographyX.whatCountry(field, value)`: Get the country related to the `field` and its `value`.
- `GeographyX.await weatherCountry(country)`: Get weather in this country related to the `country`.

## Information you can obtain

You can obtain information (fields) such as:
- Population,
- Capital,
- Calling Code,
- Initial,
- Area,
- GDP,
- Languages,
- Latitude,
- Longitude,
- Map,
- Continent,
- TimeZone,
- Flag

## Example

```javascript
        import * as GeographyX from "https://bgsn-files.web.app/geographyx/geographyx.js";
        
        async function main() {
            try {
                // Vérification du token
                const MyToken = await GeographyX.Auth("AdminTest-Token"); 

                // Utilisation de VerifAuth pour vérifier un jeton =>
                const TokenToVerif = await GeographyX.VerifAuth("AdminTest-Token");
        
                // Informations utiles pour chaque pays =>
                const capital = await GeographyX.getCountryInfo('Switzerland', 'capital');
                // Afficher dans la console
                console.log(capital);
        
                // Toutes les informations utiles pour un pays =>
                const infos = await GeographyX.getCountryInfo('Switzerland');
                // Afficher dans la console
                console.log(infos);
        
                // Tous les pays =>
                const allCountries = GeographyX.getAllCountries(await GeographyX.fetchCountryData());
                // Afficher dans la console
                console.log(allCountries);
        
                // Pays avec une valeur de champ spécifique =>
                const countriesWithLanguages = await GeographyX.whatCountry('initial', 'CH');
                // Afficher dans la console
                console.log(countriesWithLanguages);

                // Données météorologiques pour un pays =>
                const weatherData = await GeographyX.weatherCountry('Switzerland');
                if (weatherData) {
                    weatherData.forEach(weather => {
                        console.log("Temperature:", weather.temperature);
                        console.log("Description:", weather.description);
                        console.log("Humidity:", weather.humidity);
                        console.log("Pressure:", weather.pressure);
                        console.log("Wind Speed:", weather.windSpeed);
                    });
                }

            } catch (error) {
                console.error(error.message);
            }
        }

        main();
```

## Disclaimer

The data is sourced from third-party sources and may not always be up-to-date. Please verify the accuracy of the information provided before using it in a production project.

## License

The SDK GeographyX is licensed under the MIT License.

## Contact

You can contact us via email at `bougsoon.studio@gmail.com`.
```txt
Maded and powered by BougSoon Studio // https://bougsoon-studio.xyz.wf
-- © BougSoon Studio 2023 - All rights reserved
```
