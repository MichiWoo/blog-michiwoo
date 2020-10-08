<template lang="pug">
  div(class='w-full flex flex-col justify-center items-center content-center min-h-full')
    Header
    <Nuxt />
    Footer
</template>

<script>
export default {
  components: {
    Header: () => import('../components/Header.vue'),
    Footer: () => import('../components/Footer.vue'),
  },
}
</script>

<style></style>
