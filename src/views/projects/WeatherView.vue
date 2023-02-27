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
      <div class="weather-body" :class="{'has-content': hasContent}">
        <div v-if="weatherData" class="text-slate-700 mt-4">
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
        <div v-else-if="isLoading" class="flex justify-center scale-50">
          <div class="spinner">
            <div class="spinner-roll">
              <div></div>
            </div>
          </div>
        </div>
        <div v-else-if="notFound" class="text-slate-700 mt-4 flex flex-col gap-2 text-center">
          <img src="@/assets/images/weather-404.png" alt="City not found">
          <p class="text-2xl font-bold">Location not found.</p>
        </div>
      </div>
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
        isLoading: false,
        weatherData: null,
        notFound: false,
      }
    },
    computed: {
      hasContent() {
        if (this.isLoading || this.weatherData != null || this.notFound) {
          return true
        } else {
          return false
        }
      }
    },
    methods: {
      findWeather() {
        if (!this.city) {
          this.weatherData = null
          this.notFound = false
          return
        }
        this.isLoading = true
        axios
          .get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${this.openWeatherKey}&units=metric`)
          .then((res:any) => {
            this.weatherData = res.data
            this.isLoading = false
          }).catch((err:any) => {
            console.log(err)
            this.notFound = true
            this.isLoading = false
          })
      }
    }
  }
</script>


<style scoped>
  .weather-body {
    max-height: 0;
    transition: max-height 0.3s ease-out;
    overflow: hidden;
  }
  .weather-body.has-content {
    max-height: 500px;
    transition: max-height 0.3s ease-in;
    
  }

  @keyframes spinner-roll {
    0% { transform: translate(-50%,-50%) rotate(0deg); }
    100% { transform: translate(-50%,-50%) rotate(360deg); }
  }
  .spinner-roll div {
    position: absolute;
    width: 120px;
    height: 120px;
    border: 20px solid #10b981;
    border-top-color: transparent;
    border-radius: 50%;
  }
  .spinner-roll div {
    animation: spinner-roll 1s linear infinite;
    top: 100px;
    left: 100px
  }
  .spinner {
    width: 200px;
    height: 200px;
    display: inline-block;
    overflow: hidden;
    background: #FEFEFE;
  }
  .spinner-roll {
    width: 100%;
    height: 100%;
    position: relative;
    transform: translateZ(0) scale(1);
    backface-visibility: hidden;
    transform-origin: 0 0; /* see note above */
  }
  .spinner-roll div { box-sizing: content-box; }
</style>