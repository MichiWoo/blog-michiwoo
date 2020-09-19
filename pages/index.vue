<template lang="pug">
  Home(:blog='blog')
</template>

<script>
export default {
  components: {
    Home: () => import('../components/Home'),
  },
  async asyncData({ $content, params }) {
    const blog = await $content('blog', params.slug)
      .sortBy('index', 'asc')
      .fetch()
    return { blog }
  },
}
</script>

<style></style>
