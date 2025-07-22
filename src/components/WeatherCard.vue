<template>
  <div class="mt-6 p-4 max-w-md mx-auto bg-white rounded shadow">
    <h2 class="text-2xl font-bold">{{ data.name }}</h2>
    <p class="text-lg">{{ data.weather[0].description }}</p>
    <p class="text-5xl">{{ Math.round(data.main.temp) }}°C</p>
    <p>Humidity: {{ data.main.humidity }}%</p>
    <p>Wind: {{ data.wind.speed }} m/s</p>
  </div>
</template>

<script setup>
defineProps({
  data: Object
})
</script>