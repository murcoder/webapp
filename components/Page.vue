<template>
  <div class="page">
    <component :is="blok.component" v-for="blok in blok.body" :key="blok._uid" :blok="blok"></component>
    <div v-if="this.$route.path ==='/'" class="BlogBestOf">
      <BlogBestOf />
    </div>
  </div>
</template>

<script>
import BlogBestOf from './BlogBestOf'
export default {
  components: {
    BlogBestOf
  },
  props: ['blok']
}
</script>

<style lang="scss">

</style>
