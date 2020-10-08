<template lang="pug">
  article(class='flex flex-col pt-24 pb-8 w-3/4 border-b-2 border-gray-400')
    h1.my-8.max-w-full.m-auto.text-3xl.text-center.font-medium
      | {{ proj.title }}
    h3.py-4.text-center {{ proj.description }}
    nuxt-content(:document='proj')
</template>

<script>
import LazyHydrate from 'vue-lazy-hydration'
export default {
  components: {
    LazyHydrate,
  },
  async asyncData({ $content, params }) {
    const proj = await $content('projects', params.slug).fetch()
    return { proj }
  },
}
</script>

<style>
.nuxt-content-container {
  position: inherit;
}
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p {
  margin-bottom: 20px;
}
</style>
