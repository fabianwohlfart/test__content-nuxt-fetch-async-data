<template>
  <li>
    {{ page.title }}

    <LazyTree :id="page.id"/>
  </li>
</template>
<script>
  export default {
    props: [ 'page' ]
  }
</script>
