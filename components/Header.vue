<template lang="pug">
  header#top(class='w-full sm:w-4/5 md:w-4/5 lg:w-4/5 xs:w-4/5 flex justify-between items-center border-b-2 border-gray-100 py-6 md:justify-start md:space-x-10')
    nav#site-menu(class='w-full flex flex-col sm:flex-row justify-between items-center px-4 sm:px-6 py-1 bg-white')
      div(class='w-full sm:w-auto self-start sm:self-center flex flex-row sm:flex-none flex-no-wrap justify-between items-center')
        div.flex.justify-between.content-center
          NuxtLink(to='/' aria-label="Link Logo")
            div.mr-6
              Logo
        button#menuBtn(:class="`hamburger block sm:hidden focus:outline-none ${classOpen}`" type='button' @click='navToggle' aria-label="button menu app")
          span.hamburger__top-bun
          span.hamburger__bottom-bun
      #menu(:class="`w-full ${classflex} sm:w-auto self-end sm:self-center sm:flex flex-col sm:flex-row items-center h-full py-1 pb-4 sm:py-0 sm:pb-0 ${classHidden}`" aria-label="menu app")
        NuxtLink(class='text-pink-primary font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:pr-4 sm:py-1 sm:pt-2' @click.native='closeMenu' to='/') Home
        NuxtLink(class='text-pink-primary font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:px-4 sm:py-1 sm:pt-2' @click.native='closeMenu' to='/proyectos') Proyectos
        NuxtLink(class='text-pink-primary font-bold text-base w-full no-underline py-2 hover:text-gray-700 sm:w-auto sm:px-4 sm:py-1 sm:pt-2' @click.native='closeMenu' to='/acerca') Acerca de mí
</template>

<script>
export default {
  name: 'Header',
  components: {
    Logo: () => import('../components/Logo'),
  },
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
    closeMenu() {
      this.classHidden = 'hidden'
      this.classOpen = ''
      this.classflex = ''
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
