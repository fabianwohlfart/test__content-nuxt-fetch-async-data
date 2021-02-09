<template>
  <ul>
    <li v-for='page in pages'>
      <nuxt-link :to='page.slug'>{{ page.title }}</nuxt-link>
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
      this.pages = await this.$content().where({ nav: { $eq: true }}).fetch()
    },
  }
</script>
