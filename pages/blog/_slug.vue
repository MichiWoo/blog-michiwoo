<template lang="pug">
  main(class='flex flex-col pt-24 pb-8 w-3/4 border-b-2 border-gray-400')
    h1.my-8.max-w-full.m-auto.text-3xl.text-center.font-medium
      | {{ blo.title }}
    h3.py-4.text-center.uppercase {{ blo.description }}
    nuxt-content(:document='blo')
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const blo = await $content('blog', params.slug).fetch()
    return { blo }
  },
}
</script>

<style>
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
