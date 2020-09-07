<template lang="pug">
  main(class='flex flex-col pt-24 pb-8 w-3/4 border-b-2 border-gray-400')
    div.py-6.text-pink-800.font-bold.text-xl
      | Michel González
    div.py-6.text-justify
      p 💻 Desarrollador frontend...
    div(class='flex justify-center items-center shadow sm:shadow-md md:shadow-lg lg:shadow-xl xl:shadow-2xl mb-4' v-for='p in posts')
      div(class='flex flex-col items-center p-2')
        div.w-full(v-html='getTags(p)')
        div.w-full.mt-2 {{ p.description }}
        div.w-full.flex.justify-end.align-center.mt-2
          div.text-xs.text-gray-600 {{ p.createdAt }}
</template>

<script>
export default {
  name: 'Home',
  props: {
    posts: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    getTags(post) {
      let html = ''
      const tags = post.tags.split(' ')
      tags.map((t) => {
        html += `<span class='text-xs text-white bg-pink-800 rounded-full py-1 px-2 m-1 '>${t}</span>`
      })
      return html
    },
  },
}
</script>

<style></style>
