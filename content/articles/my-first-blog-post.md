---
title: My first Blog Post
description: Learning how to use @nuxt/content to create a blog
img: https://cdn.pixabay.com/photo/2021/12/19/20/43/clouds-6881917_640.jpg
alt: my first blog post

author:
  name: Mithu
  bio: All about Mithu
  image: https://cdn.pixabay.com/photo/2021/08/04/13/06/software-developer-6521720_960_720.jpg
---



## This is a heading

This is some more info

### This is a sub heading

This is some more info

### This is another sub heading

This is some more info

## This is another heading

This is some more info

<div class="p-4 mb-4 text-white bg-blue-500">
  This is HTML inside markdown that has a class of note
</div>


### Vue Component
<info-box>
  <template #info-box>
    This is a vue component inside markdown using slots
  </template>
</info-box>

### How To Build

```vue
<template>
  <div class=" bg-indigo-700 text-white px-8 py-3">
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
```
