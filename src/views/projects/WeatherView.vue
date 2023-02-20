
import InputText from 'primevue/inputtext';

<template>
  <div id="weather">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Weather App</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="weather-body" class="w-auto max-w-sm mt-5 mx-auto rounded-lg bg-[#FEFBE9] p-4">
      <div class="flex gap-4">
        <input type="text" placeholder="Input city" class="input w-full" />
        <button class="btn btn-primary">Search</button>
      </div>
    </section>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from 'vue';
  
</script>