<template>
  <ul v-if="pages">
    <LazyTreeItem v-for="page in pages" :key="page.id" :page="page" />
  </ul>
</template>
<script>
  export default {
    props: [ 'id' ],

    data() {
      return {
        pages: null
      }
    },

    fetchKey (getCounter) {
      return 'Tree' + getCounter('Tree')
    },

    async fetch() {
      this.pages = await this.$content({ deep: true}).where({ 'parentId': { $eq: this.id }}).fetch()
    },
  }
</script>
