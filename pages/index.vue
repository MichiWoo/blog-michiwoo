<template lang="pug">
  Home(:posts='posts')
</template>

<script>
import Home from '../components/Home'
export default {
  components: { Home },
  async asyncData({ $content, params }) {
    const posts = await $content('posts')
      .only(['title', 'slug', 'createdAt', 'description', 'index', 'tags'])
      .sortBy('index', 'asc')
      .fetch()
    return { posts }
  },
}
</script>

<style></style>
