<script setup lang="ts">
  import { RouterLink } from 'vue-router'
  defineProps<{
    title: string,
    content: string,
    image: string,
  }>()
</script>

<template>
  <RouterLink to="#">
    <div class="w-full rounded-md sm:flex sm:flex-col md:grid md:grid-cols-3 lg:grid-cols-4 gap-4 p-5 bg-slate-50 text-slate-700 shadow-md hover:shadow-xl transition-all">
      <div class="md:col-span-2 lg:col-span-3">
        <h3 class="text-xl font-bold">{{ title || '-' }}</h3>
        <p class="mt-4 line-clamp-3">{{ content || '' }}</p>
      </div>
      <div>
        <div class="flex justify-end">
          <img
            :src="getStaticImage(image)"
            :alt="`Image ${title}`"
            class="rounded-2xl object-cover shadow-md h-[80px]"
            width="150"
            height="150"
          >
        </div>
      </div>
    </div>
  </RouterLink>
</template>

<script lang="ts">
  export default {
    methods: {
      getStaticImage(img:string) {
        const blogImage = new URL(`/src/assets/images/${img}`, import.meta.url)
        return blogImage.href
      }
    }
  }
</script>