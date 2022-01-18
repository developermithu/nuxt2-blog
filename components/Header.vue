<template>
  <div class=" bg-gray-700 text-white px-8 py-3">
      <div class="flex justify-between items-center">
          <!-- Logo -->
          <div class="log font-bold uppercase"> 
              <nuxt-link to="/">Home</nuxt-link> 
         </div>

          <!-- Right Side -->
          <div class="flex gap-x-3 font-medium uppercase">
              <nuxt-link to="/" class="hover:text-gray-200"> home </nuxt-link>
              <nuxt-link to="/blog" class="hover:text-gray-200"> blog </nuxt-link>
              <nuxt-link to="/about" class="hover:text-gray-200"> About </nuxt-link>
              <nuxt-link to="/about" class="hover:text-gray-200"> About </nuxt-link>
          </div>
      </div>
  </div>
</template>

<script>
export default {
}
</script>

<style>

</style>