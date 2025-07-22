<script setup lang="ts">
</script>

<template>
  <main class="min-h-screen p-4 bg-blue-50 text-center">
    <h1 class="text-3xl font-bold mb-4">🌤️ Weather Dashboard</h1>
    <input
      v-model="city"
      @keyup.enter="getWeather"
      placeholder="Enter city"
      class="p-2 rounded border"
    />
    <button @click="getWeather" class="ml-2 px-4 py-2 bg-blue-500 text-white rounded">
      Search
    </button>

    <WeatherCard v-if="weatherData" :data="weatherData" />
  </main>
</template>

<script setup>
import { ref } from 'vue'
import WeatherCard from './components/WeatherCard.vue'

const city = ref('')
const weatherData = ref(null)

const API_KEY = import.meta.env.VITE_WEATHER_API_KEY

const getWeather = async () => {
  if (!city.value) return
  try {
    const res = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${city.value}&appid=${API_KEY}&units=metric`
    )
    const data = await res.json()
    weatherData.value = data
  } catch (error) {
    console.error(error)
  }
}
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
