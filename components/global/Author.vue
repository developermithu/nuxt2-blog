<template>
  <div>
    <img :src="author.image" class="rounded-full w-24"/>
    <div>
      <!-- <h4>Author</h4> -->
      <p>Name: {{ author.name }}</p>
      <p>Bio: {{ author.bio }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      author: {
        type: Object,
        required: true
      }
    }
  }
</script>