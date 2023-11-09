# GeographyX API Documentation

# What is GeographyX

GeographyX is a JavaScript API that enables you to retrieve detailed information about countries, access a complete list of world countries, retrieve country data based on information and obtain weather information for a country.

## Integration

To use our api, you must import the geographyx.js file via a script tag,
example:
```js
     <script type="module">
         import {
             Auth,
             getCountryInfo,
             fetchCountryData,
             getAllCountries,
             whatCountry,
             weatherCountry
         } from "https://blonality-studio.000.pe/geographyx/v2/geographyx.js";

        // rest of your script

      </script>
```

## Authentication

To use the GeographyX API, you need to authenticate with a valid user UID and token. You can obtain a token from the official website: [Get Token](https://blonality-studio.000.pe/api/get-token)

### `Auth(userUID, token)`

Verify the authenticity of the user with the provided user UID and token.

- **Parameters:**
  - `userUID` (string): User UID.
  - `token` (string): Authentication token.

- **Returns:**
  - `true` if authentication is successful.
  - `false` if authentication fails.

- **Example:**
  ```javascript
  const isAuthenticated = await Auth("MY-USER-UID", "MY-TOKEN");
  ```
  
## Geographical Information

### `fetchCountryData()`

Retrieve geographical information about countries.

- **Returns:**
  - Data about countries.

- **Example:**
  ```javascript
  const data = await fetchCountryData();
  console.log(data);
  ```

### `getCountryInfo(country, field)`

Get specific information about a country.

- **Parameters:**
  - `country` (string): Name of the country.
  - `field` (string, optional): Specific field to retrieve.

- **Returns:**
  - Information about the country.

- **Example:**
  ```javascript
  const capital = await getCountryInfo('Switzerland', 'capital');
  console.log(capital);

  const infos = await getCountryInfo('Switzerland');
  console.log(infos);
  ```

### `getAllCountries(data)`

Get a list of all countries.

- **Parameters:**
  - `data` (object): Geographical data.

- **Returns:**
  - A list of all countries.

- **Example:**
  ```javascript
  const allCountries = getAllCountries(await fetchCountryData());
  console.log(allCountries);
  ```

### `whatCountry(field, value)`

Find a country based on a specific field value.

- **Parameters:**
  - `field` (string): Field to search.
  - `value` (string): Value to match.

- **Returns:**
  - The name of the country matching the criteria.

- **Example:**
  ```javascript
  const country = await whatCountry('continent', 'Europe');
  console.log(country);
  ```

## Weather Information

### `weatherCountry(country)`

Get weather information for a specific country.

- **Parameters:**
  - `country` (string): Name of the country.

- **Returns:**
  - Weather information including temperature, description, humidity, pressure, and wind speed.

- **Example:**
  ```javascript
  const weatherData = await weatherCountry('Switzerland');
  if (weatherData) {
    weatherData.forEach(weather => {
      console.log("Temperature:", weather.temperature);
      console.log("Description:", weather.description);
      console.log("Humidity:", weather.humidity);
      console.log("Pressure:", weather.pressure);
      console.log("Wind Speed:", weather.windSpeed);
    });
  }
  ```

## Example of complet code 
```js
<script type="module">
         import {
             Auth,
             getCountryInfo,
             fetchCountryData,
             getAllCountries,
             whatCountry,
             weatherCountry
         } from "https://blonality-studio.000.pe/geographyx/v2/geographyx.js";
        
         async function main() {
             try {
                 // Token verification
                 const MyToken = await Auth("USER_UID", "USER_TOKEN");
        
                 // Useful information for each country =>
                 const capital = await getCountryInfo('Switzerland', 'capital');
                 // Show in console
                 console.log(capital);
        
                 // All useful information for a country =>
                 const info = await getCountryInfo('Switzerland');
                 // Show in console
                 console.log(info);
        
                 // All countries =>
                 const allCountries = getAllCountries(await fetchCountryData());
                 // Show in console
                 console.log(allCountries);
        
                 // Country with a specific field value =>
                 const WhichCountryIsIt = await whatCountry('continent', 'Europe');
                 // Show in console
                 console.log(WhichCountryIsIt);

                 // Weather data for a country =>
                 const weatherData = await weatherCountry('Switzerland');
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
     </script>
```
## Release note

We introducing a update with token and authentification system,
We are improving our token and authentication system to ensure better security.

## License

The SDK GeographyX is licensed under the MIT License.

## Contact

You can contact us via email at `contact@blonality-studio.000.pe`.
