<template>
  <div id="recommended-blog" class="mt-4 text-slate-700 bg-slate-50 rounded-md shadow-md">
    <div class="h-10 bg-slate-100 rounded-t-md flex items-center px-3">
      <h2 class="font-bold text-lg">Recommended Thread</h2>
    </div>
    <div class="rounded-b-md">
      <div v-for="list in listThread" :key="list.url" class="p-3 first:border-0 border-t hover:text-emerald-500 hover:font-bold">
        <RouterLink :to="list.url"
        >
          <h3 class="line-clamp-2">{{ list.title }}</h3>
        </RouterLink>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  export default {
    data() {
      return {
        listThread: [
          {
            title: 'Kelebihan dan Kekurangan VueJS',
            image: '',
            url: '#'
          },
          {
            title: 'Kelebihan dan Kekurangan ReactJS',
            image: '',
            url: '#'
          },
        ]
      }
    }
  }
</script>