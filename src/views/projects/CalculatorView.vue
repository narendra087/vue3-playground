<template>
  <div id="calc">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Calculator</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="calc-body" class="max-w-lg mt-5 mx-auto rounded-lg bg-slate-200 p-4">
      <div class="border rounded-md border-gray-500 h-10 text-gray-800 text-xl flex items-center justify-end p-2 cursor-default">
        {{ numValue }}
      </div>
      
      <div class="buttons mt-4 grid gap-4">
        <div class="operators grid grid-cols-4 gap-4">
          <div class="btn-calc">+</div>
          <div class="btn-calc">-</div>
          <div class="btn-calc">&times;</div>
          <div class="btn-calc">&divide;</div>
        </div>
        <div class="container-buttons grid gap-4">
          <div class="grid grid-rows-3 gap-4">
            <div class="numbers grid grid-cols-3 gap-4 sm">
              <div class="btn-calc">7</div>
              <div class="btn-calc">8</div>
              <div class="btn-calc">9</div>
            </div>
            <div class="numbers grid grid-cols-3 gap-4">
              <div class="btn-calc">4</div>
              <div class="btn-calc">5</div>
              <div class="btn-calc">6</div>
            </div>
            <div class="numbers grid grid-cols-3 gap-4">
              <div class="btn-calc">1</div>
              <div class="btn-calc">2</div>
              <div class="btn-calc">3</div>
            </div>
            <div class="numbers grid grid-cols-3 gap-4">
              <div class="btn-calc">C</div>
              <div class="btn-calc">0</div>
              <div class="btn-calc">.</div>
            </div>
          </div>
          <div class="btn-calc">=</div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
  import {ref } from 'vue';
  
  export default {
    setup() {
      const numValue:any = ref(0)
      
      return {
        numValue,
      }
    }
  }
  
</script>

<style>
  .btn-calc {
    @apply text-gray-900 text-xl flex items-center justify-center border border-gray-900 p-2 cursor-pointer;
  }
  
  .container-buttons {
    transition: all 0.3s;
    grid-template-columns: 3.5fr 1fr;
  }
  
  @media (min-width: 475px) {
    .container-buttons {
      grid-template-columns: 3.33fr 1fr;
    }
  }
</style>