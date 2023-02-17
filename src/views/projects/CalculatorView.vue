<template>
  <div id="calc">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Calculator</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="calc-body" class="max-w-[320px] mt-5 mx-auto rounded-lg bg-[#FEFBE9] p-4">
      <div class="calc-input border rounded-md border-gray-500 min-h-[46px] text-gray-800 text-xl flex flex-col items-end justify-end p-2 cursor-default">
        <p :class="[ calculationResult ? 'text-sm transition-all' : '', 'text-right break-all' ]">{{ stringNumber }}</p>
        <p :class="[ !calculationResult ? 'text-sm' : '', 'text-2xl font-bold transition-all text-right break-all']">{{ calculationResult }}</p>
      </div>
      
      <div class="calc-buttons mt-4 grid grid-cols-4 grid-rows-5 gap-4">
        <div class="contents">
          <div class="btn-calc btn-operator" @click="clearNumber">AC</div>
          <div class="btn-calc btn-operator" @click="setNumber('(')">(</div>
          <div class="btn-calc btn-operator" @click="setNumber(')')">)</div>
          <div class="btn-calc btn-operator" @click="setNumber('/')">&divide;</div>
        </div>
        <div class="contents">
          <div class="btn-calc btn-number" @click="setNumber('7')">7</div>
          <div class="btn-calc btn-number" @click="setNumber('8')">8</div>
          <div class="btn-calc btn-number" @click="setNumber('9')">9</div>
          <div class="btn-calc btn-operator" @click="setNumber('*')">&times;</div>
        </div>
        <div class="contents">
          <div class="btn-calc btn-number" @click="setNumber('4')">4</div>
          <div class="btn-calc btn-number" @click="setNumber('5')">5</div>
          <div class="btn-calc btn-number" @click="setNumber('6')">6</div>
          <div class="btn-calc btn-operator" @click="setNumber('-')">-</div>
        </div>
        <div class="contents">
          <div class="btn-calc btn-number" @click="setNumber('1')">1</div>
          <div class="btn-calc btn-number" @click="setNumber('2')">2</div>
          <div class="btn-calc btn-number" @click="setNumber('3')">3</div>
          <div class="btn-calc btn-operator" @click="setNumber('+')">+</div>
        </div>
        <div class="contents">
          <div class="btn-calc btn-number" @click="setNumber('00')">00</div>
          <div class="btn-calc btn-number" @click="setNumber('0')">0</div>
          <div class="btn-calc btn-operator" @click="setNumber('.')">.</div>
          <div class="btn-calc btn-operator" @click="setResults">=</div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
  import {ref } from 'vue';
  
  export default {
    setup() {
      const stringNumber:any = ref('0')
      const calculationResult:any = ref('')
      
      const setNumber = (val:string) => {
        const regexNumber = /[0-9]/
        if (stringNumber.value == '0' && regexNumber.test(val)) {
          stringNumber.value = val
        } else {
          stringNumber.value+=val
        }
      }
      
      const setResults = () => {
        calculationResult.value = '= ' + eval(stringNumber.value)
      }
      
      const clearNumber = () => {
        stringNumber.value = '0'
        calculationResult.value = ''
      }
      
      return {
        stringNumber,
        setNumber,
        clearNumber,
        calculationResult,
        setResults,
      }
    }
  }
  
</script>

<style>
  .btn-calc {
    @apply text-gray-900 text-lg flex items-center justify-center border border-gray-900 p-2 cursor-pointer rounded-md;
  }
  
  .btn-number {
    background-color: #E1EEDD;
  }
  .btn-operator {
    background-color: #F0A04B;
  }
</style>