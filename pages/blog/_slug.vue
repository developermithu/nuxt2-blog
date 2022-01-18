<template>
  <div>
    <Header />

    <article class="p-5 w-11/12 sm:w-8/12 m-auto">
      <!-- <pre> {{ article }} </pre> -->

      <h1 class="text-3xl font-bold">{{ article.title }}</h1>

      <img :src="article.img" :alt="article.alt" class="py-3" />
      <p>
        Last updated:
        <span class="font-semibold">{{ formatDate(article.updatedAt) }}</span>
      </p>

      <!-- <p> {{ article.description }} </p> -->

      <author :author="article.author" />

      <nav>
        <ul>
          <li v-for="link of article.toc" :key="link.id">
            <NuxtLink
              class="hover:underline text-sm font-semibold text-blue-500 pt-5"
              :class="{
                'py-2': link.depth === 2,
                'ml-2 pb-2': link.depth === 3,
              }"
              :to="`#${link.id}`"
              >{{ link.text }}</NuxtLink
            >
          </li>
        </ul>
      </nav>

      <!-- Markdown -->
      <nuxt-content :document="article" class="text-gray-700 text-sm py-5" />
    </article>

    <!-- Prev Next Button -->
    <prev-next :prev="prev" :next="next" />

    <Footer />
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: this.article.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.article.description,
        },
      ],
    };
  },

  async asyncData({ $content, params }) {
    const article = await $content("articles", params.slug).fetch();

    const [prev, next] = await $content("articles")
      .only(["title", "slug"])
      .sortBy("createdAt", "asc")
      .surround(params.slug)
      .fetch();

    return {
      article,
      prev,
      next,
    };
  },

  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>

<style>
.nuxt-content h1 {
  @apply text-2xl font-bold;
}
.nuxt-content h2 {
  @apply text-xl font-bold;
}
.nuxt-content h3 {
  @apply text-lg font-bold;
}
.nuxt-content p {
  @apply mb-5 mt-2;
}
</style>