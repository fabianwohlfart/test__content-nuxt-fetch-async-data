<template>
  <ul>
    <li v-for='page in pages'>
      <nuxt-link :to='`/${page.slug}/`'>{{ page.title }}</nuxt-link>
    </li>
  </ul>
</template>
<script>
  export default {
    data() {
      return {
        pages: []
      }
    },

    async fetch() {
      const pages = await this.$content().fetch()
      this.pages = pages
    },

    created () {
      /*
      * If this is not fetching on created()
      * then it wont load,
      * if this component is not on a page which was initally loaded
      */
      this.$fetch()
    }
  }
</script>
