<template>
  <div id="menu">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Welcome to Vue3 Playground</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="content" class="pt-5">
      <p class="text-lg mb-5">Project List:</p>
      <div class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 gap-5">
        <ProjectCard title="Calculator" name="calculator" image="" />
        <!-- <ProjectCard title="To-do-list" name="" image="" /> -->
        <ProjectCard title="Weather" name="weather" image="" />
        <ProjectCard title="Blog" name="blog" image="" />
        <ProjectCard title="Forum" name="" image="" />
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
  import ProjectCard from '@/components/ProjectCard.vue';
</script>