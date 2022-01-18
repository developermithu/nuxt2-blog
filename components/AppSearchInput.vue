<template>
  <div>
    <input
      v-model="searchQuery"
      type="search"
      autocomplete="off"
      placeholder="Search Articles"
      class="
        bg-gray-200
        py-2.5
        px-4
        rounded
        w-full
        focus:outline-none focus:ring-2 focus:ring-indigo-900
      "
    />
    <ul v-if="articles.length" class="bg-gray-700 text-sm text-gray-300 flex flex-col gap-y-3 py-3 mt-1 rounded">
      <li v-for="article of articles" :key="article.slug" class="hover:bg-gray-500 block w-full py-1 px-3 ">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          {{ article.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      articles: [],
    };
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery) {
        this.articles = [];
        return;
      }
      this.articles = await this.$content("articles")
        .limit(6)
        .search(searchQuery)
        .fetch();
    },
  },
};
</script>