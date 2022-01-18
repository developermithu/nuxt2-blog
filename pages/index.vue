<template>
  <div>
    <Header />

    <!-- <Tutorial/> -->
    <div class="p-8 w-10/12 sm:w-8/12 m-auto">
      <div class="w-10/12 sm:w-8/12 m-auto">
  <AppSearchInput />
      </div>

      <!-- Card -->
      <div v-for="article of articles" :key="article.slug" class="mt-6 w-10/12 sm:w-8/12 m-auto shadow-lg rounded">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
                <img
                  :src="article.img"
                  alt=""
                  class="w-full"
                />
                <div class="p-5">
                  <h3
                    class="text-md font-bold text-gray-700 hover:underline capitalize"
                  >
                    <nuxt-link :to="{ name: 'blog-slug', params: { slug: article.slug } }">
                      {{ article.title }}
                    </nuxt-link>
                  </h3>
                  <p class="text-sm text-gray-500 font-semibold">{{ article.author.name }}</p>
                  <p class="text-xs text-gray-500 pt-3">{{ article.description }}</p>
                </div>
        </NuxtLink>
      </div>

    </div>

    <Footer />
  </div>
</template>

<script>
import Header from "../components/Header.vue";
export default {
  components: { Header },
  name: "IndexPage",

  async asyncData({ $content, params }) {
    const articles = await $content("articles")
      .only(["title", "description", "img", "slug", "author"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      articles,
    };
  },

  head() {
    return {
      title: "Home",
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content: "Nuxt 2 blog app - developed by mithu",
        },
      ],
    };
  },
};
</script>
