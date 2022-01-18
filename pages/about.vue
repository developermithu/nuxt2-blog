<template>
<div>
      About Us
</div>
</template>

<script>
export default {
    head() {
      return {
        title: 'About Us',
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'description',
            name: 'description',
            content: 'About us page'
          }
        ]
      }
    }
}
</script>

<style>

</style>