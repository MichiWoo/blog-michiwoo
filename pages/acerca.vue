<template lang="pug">
  main(class='flex flex-col py-8 w-3/4 border-b-2 border-gray-400')
    div.py-6.text-pink-primary.font-bold.text-xl
      | ✋ Soy Michel González
    div.py-6.text-justify
      p 💻 Desarrollador frontend, en el mundo digital me encuentras como 
        b.text-pink-primary Michiwoo.
    div.py-6.text-justify
      | Las tecnologías con las que trabajo actualmente son:
    ul(class='w-full flex flex-wrap justify-center items-center ')
      Tooltip(v-for='icon in icons' :icon="icon" :key="icon.id")
</template>

<script>
export default {
  name: 'Acerca',
  components: {
    Tooltip: () => import('../components/Tooltip'),
  },
  data() {
    return {
      icons: [
        {
          id: 1,
          categoria: 'frontend',
          path: 'icons/html-5.svg',
          alt: 'HTML',
        },
        {
          id: 2,
          categoria: 'frontend',
          path: 'icons/css-3_official.svg',
          alt: 'CSS',
        },
        {
          id: 3,
          categoria: 'frontend',
          path: 'icons/javascript.svg',
          alt: 'Javascript',
        },
        {
          id: 4,
          categoria: 'backend',
          path: 'icons/mysql.svg',
          alt: 'MySql',
        },
        {
          id: 5,
          categoria: 'backend',
          path: 'icons/mariadb-icon.svg',
          alt: 'MariaDB',
        },
        {
          id: 6,
          categoria: 'backend',
          path: 'icons/php.svg',
          alt: 'PHP',
        },
        {
          id: 7,
          categoria: 'backend',
          path: 'icons/c-sharp.svg',
          alt: 'C-SHARP',
        },
        {
          id: 8,
          categoria: 'backend',
          path: 'icons/nodejs.svg',
          alt: 'Node',
        },
        {
          id: 9,
          categoria: 'frameworks',
          path: 'icons/vue.svg',
          alt: 'VUE',
        },
        {
          id: 10,
          categoria: 'frameworks',
          path: 'icons/react.svg',
          alt: 'React',
        },
        {
          id: 11,
          categoria: 'frameworks',
          path: 'icons/svelte-icon.svg',
          alt: 'Svelte',
        },
      ],
    }
  },
}
</script>

<style></style>
