<template lang="pug">
  main(class='flex flex-col pt-24 pb-8 w-3/4 border-b-2 border-gray-400')
    div.py-6.text-pink-800.font-bold.text-xl
      | Michel González
    div.py-6.text-justify
      p 💻 Desarrollador frontend...
    div(class='grid gap-2 grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-4')
      NuxtLink(v-for='p in blog' :key='p.index' :to="`/blog/${p.slug}`")
        div(class='max-w-sm rounded overflow-hidden shadow-lg card py-4')
          div.overlay
          div.px-6.py-4
            div.font-bold.text-xl.mb-2 
              span {{ p.title }}
            p.text-gray-700.text-base
              | {{ p.description }}
          div.px-6.pt-4.pb-2
            span(v-html='getTags(p)')
          div.w-full.flex.justify-end.align-center.mt-2
            div.text-xs.text-gray-600.pr-3.pb-1 {{ normalizedDate(p.createdAt) }}
</template>

<script>
export default {
  name: 'Home',
  props: {
    blog: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    getTags(blog) {
      let html = ''
      const tags = blog.tags.split(' ')
      tags.map((t) => {
        html += `<span class='inline-block bg-pink-800 rounded-full px-3 py-1 text-sm font-semibold text-white mr-2 mb-2'>${t}</span>`
      })
      return html
    },
    normalizedDate(createdAt) {
      const date = new Date(createdAt)
      const normalizedCreatedAt = new Intl.DateTimeFormat('es-Mx').format(date)
      return normalizedCreatedAt
    },
  },
}
</script>

<style>
.card {
  --box-shadow-color: rgba(151, 38, 109, 0.6);
}
.card:hover {
  cursor: pointer;
  transform: translateY(-5px) scale(1.005) translateZ(0);
  box-shadow: 0 6px 10px rgba(0, 0, 0, 0.11), 0 6px 12px var(--box-shadow-color);
}

.card:hover .overlay {
  transform: scale(4) translateZ(0);
}
</style>
