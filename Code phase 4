<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Weather Dashboard</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        background: linear-gradient(to right, #4facfe, #00f2fe);
        margin: 0;
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
        min-height: 100vh;
        color: #fff;
      }
      header {
        margin: 20px;
        font-size: 2em;
        font-weight: bold;
      }
      .search-box {
        margin: 20px;
      }
      input {
        padding: 10px;
        border: none;
        border-radius: 5px;
        width: 250px;
      }
      button {
        padding: 10px;
        border: none;
        border-radius: 5px;
        background: #0066ff;
        color: #fff;
        cursor: pointer;
        margin-left: 10px;
      }
      button:hover {
        background: #0047b3;
      }
      .weather-info {
        margin-top: 20px;
        background: rgba(255, 255, 255, 0.1);
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        text-align: center;
        width: 300px;
      }
      .weather-info h2 {
        margin: 10px 0;
      }
    </style>
  </head>
  <body>
    <header>🌤️ Weather Dashboard</header>
    <div class="search-box">
      <input type="text" id="cityInput" placeholder="Enter city name" />
      <button onclick="getWeather()">Search</button>
    </div>
    <div class="weather-info" id="weatherInfo">
      <p>Search for a city to see weather details</p>
    </div>

    <script>
      // 🔑 Replace with your real OpenWeatherMap API key
      const apiKey = "b8e4e2b5b7fe01a9566a19c8e2ac818a";

      async function getWeather() {
        const city = document.getElementById("cityInput").value.trim();
        if (!city) {
          alert("Please enter a city name");
          return;
        }

        // Use encodeURIComponent to handle spaces and special characters in city names
        const url = `https://api.openweathermap.org/data/2.5/weather?q=${encodeURIComponent(
          city
        )}&appid=${apiKey}&units=metric`;

        try {
          const response = await fetch(url);
          const data = await response.json();

          if (data.cod !== 200) {
            throw new Error(data.message);
          }

          document.getElementById("weatherInfo").innerHTML = `
          <h2>${data.name}, ${data.sys.country}</h2>
          <p><strong>Temperature:</strong> ${data.main.temp} °C</p>
          <p><strong>Weather:</strong> ${data.weather[0].description}</p>
          <p><strong>Humidity:</strong> ${data.main.humidity}%</p>
          <p><strong>Wind Speed:</strong> ${data.wind.speed} m/s</p>
        `;
        } catch (error) {
          document.getElementById(
            "weatherInfo"
          ).innerHTML = `<p style="color: red;">${error.message}</p>`;
        }
      }
    </script>
  </body>
</html>
