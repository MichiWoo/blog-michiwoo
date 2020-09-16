<template lang="pug">
  Home(:blog='blog')
</template>

<script>
import Home from '../components/Home'
export default {
  components: { Home },
  async asyncData({ $content, params }) {
    const blog = await $content('blog', params.slug)
      .sortBy('index', 'asc')
      .fetch()
    return { blog }
  },
}
</script>

<style></style>
