<template lang="pug">
  footer.w-full.pt-3.pb-6
    div(class="flex flex-col justify-center")
      div(class="flex justify-around content-center mb-2")
        div(class="flex justify-center content-center")
          a(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2") Home
        div(class="flex justify-center content-center")
          a(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2") Blog
        div(class="flex justify-center content-center")
          a(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2") Proyectos
        div(class="flex justify-center content-center")
          a(class="text-pink-800 font-bold no-underline py-2 hover:text-gray-700 sm:w-auto text-sm sm:py-1 sm:pt-2") Acerca de mí
      div.flex.justify-center.content-center.mb-2
        div(class="flex justify-center content-center mx-3")
          button(class="rounded-full h-8 w-8 flex items-center justify-center bg-pink-800 text-white hover:bg-purple-700")
              font-awesome-icon(:icon="['fab', 'twitter']")
        div(class="flex justify-center content-center mx-3")
          button(class="rounded-full h-8 w-8 flex items-center justify-center bg-pink-800 text-white hover:bg-purple-700")
            font-awesome-icon(:icon="['fab', 'github']")
        div(class="flex justify-center content-center mx-3")
          button(class="rounded-full h-8 w-8 flex items-center justify-center bg-pink-800 text-white hover:bg-purple-700")
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
