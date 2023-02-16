<template>
  <div class="card p-3 min-h-[150px] rounded-lg border border-emerald-500 cursor-pointer flex justify-center items-center">
    <p class="text-xl">{{title}}</p>
  </div>
</template>

<script setup lang="ts">
  defineProps<{
    title: string,
    image: any,
  }>()
</script>

<style scoped>
  .card {
    transition: all 0.5s;
  }
  .card:hover {
    box-shadow: 0 0 10px 5px rgba(16,185,129,0.39);
  }
</style>