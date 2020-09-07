<template lang="pug">
  main(class='flex flex-col py-24 w-3/4 border-b-2 border-gray-400')
    div.py-6.text-pink-800.font-bold.text-xl
      | ✋ Soy Michel González
    div.py-6.text-justify
      p 💻 Desarrollador frontend, en el mundo digital me encuentras como 
        b.text-pink-800 Michiwoo
        | , actualmente desarrollo con Vue.
    div.py-6.text-justify
      p 💚 Amo ver series, la tecnología y mi meta es Nunca dejar de aprender.
    div.py-6.text-center
      | Si tienes algún proyecto, puedes encontrarme en mis redes sociales: 
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
</template>

<script>
export default {
  name: 'Acerca',
}
</script>

<style></style>
