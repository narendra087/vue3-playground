<template>
  <RouterLink :to="{ name: name || '' }">
    <div class="project-card p-3 min-h-[150px] rounded-lg border border-emerald-500 cursor-pointer flex flex-col justify-center items-center">
      <p class="text-xl">{{title}}</p>
      <span v-if="!name" class="text-sm">( coming soon )</span>
    </div>
  </RouterLink>
</template>

<script setup lang="ts">
  import { RouterLink } from 'vue-router'
  defineProps<{
    title: string,
    name: string,
    image: any,
  }>()
</script>

<style scoped>
  .project-card {
    transition: all 0.5s;
  }
  .project-card:hover {
    box-shadow: 0 0 10px 5px rgba(16,185,129,0.39);
  }
</style>