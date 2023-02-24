<template>
  <div id="blog">
    <section id="about" class="flex flex-col gap-1 md:gap-3 items-center">
      <h1 class="md:text-3xl sm:text-2xl text-xl text-center">Blog</h1>
      <p class="text-emerald-500">Made by Narendra.</p>
    </section>
    
    <section id="blog-body" class="w-auto mt-5 mx-auto rounded-lg bg-[#FEFEFE] p-4 max-h-[768px] overflow-auto">
      <div class="blog-header text-slate-700 flex flex-col">
        <h2 class="text-3xl font-bold w-full border-b py-4">Frontend Blog</h2>
        <div class="blog-category tabs items-start border-b">
          <div
            v-for="blog in blogCategory"
            :key="blog.slug"
            class="tab"
            :class="{'tab-active': blog.slug == activeTab}"
            @click="$event => changeCategory(blog.slug)"
          >
            {{ blog.name }}
          </div>
        </div>
      </div>
      <div class="blog-content p-5 grid grid-cols-4 gap-4 -mx-4 -mb-4 bg-slate-200 rounded-b-lg">
        <div class="col-span-3 flex flex-col gap-4 px-4">
          <div class="blog-filter">
            <select class="select select-ghost w-full max-w-xs text-slate-700">
              <option>Latest thread</option>
              <option>Popular thread</option>
            </select>
          </div>
          <div class="blog-list flex flex-col gap-4">
            <BlogCard
              v-for="blog in blogList"
              :key="blog.title"
              :title="blog.title"
              :content="blog.content"
              :image="blog.image"
            />
          </div>
        </div>
        <div class="">
          <button class="btn btn-block">Buat thread</button>
          <RecommendedBlog />
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts" setup>
  import { blogCategory } from '../../mock/blogCategory'
  import { blogList } from '../../mock/blogList'
  
  import BlogCard from '@/components/BlogCard.vue';
  import RecommendedBlog from '@/components/blog/RecommendedBlog.vue';
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
    },
    mounted() {
      console.log(this.blogList)
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