<template lang="pug">
  header#top.w-full.flex.flex-col.fixed.bg-white(class='sm:relative')
    nav#site-menu(class='flex flex-col sm:flex-row w-full justify-between items-center px-4 sm:px-6 py-1 bg-white shadow sm:shadow-md')
      div(class='w-full sm:w-auto self-start sm:self-center flex flex-row sm:flex-none flex-no-wrap justify-between items-center')
        div.flex.justify-between.content-center
          Logo
          span.font-semibold.text-gray-700.text-xl.tracking-tight.my-auto Michiwoo
        button#menuBtn(:class="`hamburger block sm:hidden focus:outline-none ${classOpen}`" type='button' @click='navToggle')
          span.hamburger__top-bun
          span.hamburger__bottom-bun
      #menu(:class="`w-full ${classflex} sm:w-auto self-end sm:self-center sm:flex flex-col sm:flex-row items-center h-full py-1 pb-4 sm:py-0 sm:pb-0 ${classHidden}`")
        a(class='text-pink-800 font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:pr-4 sm:py-1 sm:pt-2') Home
        a(class='text-pink-800 font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:px-4 sm:py-1 sm:pt-2') Blog
        a(class='text-pink-800 font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:px-4 sm:py-1 sm:pt-2') Proyectos
        a(class='text-pink-800 font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:px-4 sm:py-1 sm:pt-2') Acerca de mí
</template>

<script>
import Logo from '../components/Logo'
export default {
  name: 'Header',
  components: { Logo },
  data() {
    return {
      classflex: '',
      classHidden: 'hidden',
      classOpen: '',
    }
  },
  methods: {
    navToggle() {
      this.classflex === 'flex'
        ? (this.classflex = '')
        : (this.classflex = 'flex')
      this.classHidden === 'hidden'
        ? (this.classHidden = '')
        : (this.classHidden = 'hidden')
      this.classOpen === 'open'
        ? (this.classOpen = '')
        : (this.classOpen = 'open')
    },
  },
}
</script>

<style>
.hamburger {
  cursor: pointer;
  width: 48px;
  height: 48px;
  transition: all 0.25s;
}

.hamburger__top-bun,
.hamburger__bottom-bun {
  content: '';
  position: absolute;
  width: 24px;
  height: 2px;
  background: #000;
  transform: rotate(0);
  transition: all 0.5s;
}

.hamburger:hover [class*='-bun'] {
  background: #333;
}

.hamburger__top-bun {
  transform: translateY(-5px);
}

.hamburger__bottom-bun {
  transform: translateY(3px);
}

.open {
  transform: rotate(90deg);
  transform: translateY(-1px);
}

.open .hamburger__top-bun {
  transform: rotate(45deg) translateY(0px);
}

.open .hamburger__bottom-bun {
  transform: rotate(-45deg) translateY(0px);
}
</style>
