<template lang="pug">
  footer(class="sm:w-4/5 md:w-4/5 lg:1/4 xl:w-1/4 pt-3 pb-6")
    div(class="flex flex-col justify-center")
      div(class="flex justify-around content-center mb-2")
        div(class="flex justify-center content-center")
          NuxtLink(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2" to='/') Home
        div(class="flex justify-center content-center")
          NuxtLink(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2" to='/blog') Blog
        div(class="flex justify-center content-center")
          NuxtLink(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2" to='/proyectos') Proyectos
      div.flex.justify-center.content-center.mb-2
        div(class="flex justify-center content-center mx-3")
          a(class="rounded-full h-8 w-8 flex items-center justify-center bg-pink-800 text-white hover:bg-purple-700" href='https://twitter.com/MichiwooWebs' target='_blank' rel='noreferer noopener')
            font-awesome-icon(:icon="['fab', 'twitter']")
        div(class="flex justify-center content-center mx-3")
          a(class="rounded-full h-8 w-8 flex items-center justify-center bg-pink-800 text-white hover:bg-purple-700" href='https://github.com/MichiWoo' target='_blank' rel='noreferer noopener')
            font-awesome-icon(:icon="['fab', 'github']")
        div(class="flex justify-center content-center mx-3")
          a(class="rounded-full h-8 w-8 flex items-center justify-center bg-pink-800 text-white hover:bg-purple-700" href='mailto:michiwoo.web@gmail.com?subject=Desarrollemos%20algo%20espectacular')
            font-awesome-icon(:icon="['fas', 'envelope']")
      div.flex.justify-center.content-center
        span Hecho con 💜 por&nbsp 
        a(class="text-pink-800") michiwoo
        | &nbsp© 2020
</template>

<script>
export default {
  name: 'Footer',
}
</script>

<style></style>
