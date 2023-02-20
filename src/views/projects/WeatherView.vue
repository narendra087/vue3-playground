<template>
  <div id="weather">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Weather App</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="weather-body" class="w-auto max-w-sm mt-5 mx-auto rounded-lg bg-[#FEFEFE] p-4">
      <div class="flex gap-2">
        <input type="text" placeholder="Enter city name" class="input w-full" v-model="city" @keyup.enter="findWeather" />
        <button class="btn btn-primary" @click="findWeather">Search</button>
      </div>
      <div v-if="weatherData != null" class="text-slate-700 mt-4">
        <h2 class="font-bold">Weather in {{ weatherData?.name }}</h2>
        <p class="text-2xl font-bold">{{ weatherData?.main?.temp }}&deg;C</p>
        <div class="flex gap-2 items-center">
          <img
            :src="`http://openweathermap.org/img/wn/${weatherData?.weather[0]?.icon}@2x.png`"
            alt="weather image"
            width="150"
            height="150"
          >
          <div class="flex flex-col">
            <p class="font-bold text-xl">{{ weatherData?.weather[0]?.main }}</p>
            <span class="text-sm ">( {{ weatherData?.weather[0]?.description }} )</span>
          </div>
        </div>
        <p class="mt-4">Humidity: <span class="font-bold">{{ weatherData?.main?.humidity }}%</span></p>
        <p>Wind: <span class="font-bold">{{ weatherData?.wind?.speed }} km/h</span></p>
      </div>
      <div v-else class=""></div> 
    </section>
  </div>
</template>

<script lang="ts">
  import axios from 'axios'
  
  export default {
    data():any {
      return {
        openWeatherKey: import.meta.env.VITE_OPENWEATHER_KEY || '',
        city: '',
        weatherData: null,
      }
    },
    methods: {
      findWeather() {
        if (!this.city) {
          this.weatherData = null
        }
        axios
          .get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${this.openWeatherKey}&units=metric`)
          .then((res:any) => {
            this.weatherData = res.data
          }).catch((err:any) => {
            console.log(err)
          })
      }
    }
  }
</script>