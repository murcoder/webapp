<template>
  <section>
    <component v-if="story && story.content && story.content.component" :key="story.content._uid" :blok="story.content" :is="story.content.component"></component>
 </section>
</template>

<script>
import storyblokLivePreview from '@/mixins/storyblokLivePreview'

export default {
  computed: {
    pressInfo () {
      return this.story.content
    }
  },
  data () {
    return {
      story: null
    }
  },
  mixins: [storyblokLivePreview],
  asyncData (context) {
    return context.store.dispatch('loadFullPage', context.route.fullPath).catch((e) => {
      context.error({ statusCode: e.response.status, message: e.response.statusText })
    })
  }
}
</script>
