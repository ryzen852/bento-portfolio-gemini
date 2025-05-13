<template>
  <div class="card bg-dark text-white overflow-hidden">
    <img :src="backgroundImageUrl" class="card-img opacity-50" alt="Location Image" />
    <div class="card-img-overlay d-flex flex-column justify-content-end">
      <h5 class="card-title">
        <img :src="weatherData.icon" width="50" />
        {{ weatherData.temperature }}°C {{ weatherData.description }}
      </h5>
      <p class="card-text">{{ weatherData.location }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const weatherData = ref({
  location: "Loading...",
  temperature: "...",
  description: "Loading...",
});

const backgroundImageUrl = ref('');

// Function to calculate the image URL based on time
const updateBackgroundImage = () => {
  const hours = new Date().getHours();
  let pickNight = '';
  pickNight = hours >= 6 && hours < 20 ? '' : '_night';

  backgroundImageUrl.value = new URL(
    `../assets/van${pickNight}.jpg`,
    import.meta.url
  ).href;
};

onMounted(async () => {
  // Fetch location and weather data from APIs
  // Replace with your actual API calls and logic
  updateBackgroundImage();
  try {
    // Example API calls (replace with your chosen APIs)
    const apiKey = import.meta.env.VITE_OPENWEATHER_API_KEY;
    const locationJson = {
      city: "Vancouver",
      country: "Canada",
      latitude: 49.246292,
      longitude: -123.116226,
    };
    weatherData.value.location = `${locationJson.city}, ${locationJson.country}`;

    const weatherResponse = await fetch(
      `https://api.openweathermap.org/data/3.0/onecall?lat=${locationJson.latitude}&lon=${locationJson.longitude}&appid=${apiKey}`
    );
    const weatherJson = await weatherResponse.json();
    weatherData.value.temperature = Math.round(
      weatherJson.current.temp - 273.15
    ); // Example: Convert Kelvin to Celsius
    weatherData.value.icon = `https://openweathermap.org/img/wn/${weatherJson.current.weather[0].icon}@2x.png`;
    weatherData.value.description = weatherJson.current.weather[0].description;
  } catch (error) {
    console.error("Error fetching weather or location data:", error);
    weatherData.value.location = "Location not available";
    weatherData.value.temperature = "--";
    weatherData.value.description = "Weather not available";
  }
});

</script>

<style scoped>
.card-img {
  object-fit: cover;
  height: 100%;
  width: 100%;
}

.card-img-overlay {
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.7),
    transparent
  ); /* Gradient overlay for text readability */
}
</style>
