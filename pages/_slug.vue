<template>
  <div>
    {{ payload.title }}
    <nuxt-link to='/'>Back</nuxt-link>
  </div>
</template>
<script>
  export default {
    async asyncData ({ $content, params }) {
      const payload = await $content(params.slug, { deep: true }).fetch()
      return {
        payload: payload
      }
    }
  }
</script>
