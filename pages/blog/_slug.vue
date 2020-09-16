<template lang="pug">
  article(class='flex flex-col pt-24 pb-8 w-3/4 border-b-2 border-gray-400')
    h1.my-8.max-w-full.m-auto.text-3xl.text-center.font-medium
      | {{ blo.title }}
    h3.py-4.text-center {{ blo.description }}
    small.text-pink-800.font-bold {{ `Actualización: ${formatDate(blo.updatedAt)}`}}
    div.flex.flex-start
      button.bg-transparent.text-pink-800.py-1.px-1.rounded-full(@click='verContenido' v-show='!showContenido')
        | Ver Contenido
        .icon.icon-down
      button.bg-transparent.text-pink-800.py-1.px-1.rounded-full(@click='verContenido' v-show='showContenido')
        | Ocultar Contenido
        .icon.icon-up
    nav(v-show='showContenido')
      ul
        li(v-for="link of blo.toc" :key="link.id")
          NuxtLink(:class="{ 'py-2': link.depth === 2, 'ml-2 pb-2': link.depth === 3 }" :to="`#${link.id}`") {{ link.text }}
    div.separator
    nuxt-content(:document='blo')
    prev-next(:prev="prev" :next="next")
  </template>

<script>
export default {
  async asyncData({ $content, params }) {
    const blo = await $content('blog', params.slug).fetch()
    const [prev, next] = await $content('blog')
      .only(['title', 'slug'])
      .sortBy('index', 'asc')
      .surround(params.slug)
      .fetch()
    return { blo, prev, next }
  },
  data() {
    return {
      showContenido: false,
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
    verContenido() {
      this.showContenido === true
        ? (this.showContenido = false)
        : (this.showContenido = true)
    },
  },
}
</script>

<style>
.separator {
  margin-bottom: 30px;
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
.icon.icon-link {
  background-image: url('~assets/svg/icon-hashtag.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}

.icon.icon-down {
  background-image: url('~assets/svg/icon-cheveron-down.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}
.icon.icon-up {
  background-image: url('~assets/svg/icon-cheveron-up.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}
</style>
