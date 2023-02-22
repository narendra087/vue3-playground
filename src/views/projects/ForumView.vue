<template>
  <div id="forum">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Forum</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="forum-body" class="w-auto mt-5 mx-auto rounded-lg bg-[#FEFEFE] p-4">
      <div class="forum-header text-slate-700 flex flex-col">
        <h2 class="text-3xl font-bold w-full border-b py-4">Frontend Developer Forum</h2>
        <div class="forum-category tabs items-start border-b">
          <div
            v-for="forum in forumCategory"
            :key="forum.slug"
            class="tab"
            :class="{'tab-active': forum.slug == activeTab}"
            @click="$event => changeCategory(forum.slug)"
          >
            {{ forum.name }}
          </div>
        </div>
      </div>
      <div class="forum-content"></div>
    </section>
  </div>
</template>

<script lang="ts" setup>
  import { forumCategory } from '../../mock/forumCategory'
</script>

<script lang="ts">
  export default {
    data():any {
      return {
        activeTab: '',
      }
    },
    methods: {
      changeCategory(val: string) {
        this.activeTab = val
      }
    }
  }
</script>

<style>
  .tab {
    @apply text-slate-400;
  }
  .tab-active {
    @apply text-teal-700 font-bold border-b-teal-700 border-b-2;
  }
  .tab:hover:not(.tab-active) {
    @apply text-slate-700;
  }
</style>