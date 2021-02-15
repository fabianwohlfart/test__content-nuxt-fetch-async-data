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
      this.pages = await this.$content().fetch()
    },

    created () {
      /*
      * I this component is not on a page which was initally loaded (not on page-b / _slug.vue)
      * its not loaded properly when we navigate to it (index.vue)
      * Therefor we have to fetch it manually
      * Fetching manually loads the whole DB...
      */
      this.$fetch()
    }
  }
</script>
