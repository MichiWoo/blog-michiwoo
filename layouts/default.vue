<template lang="pug">
  div(class='w-full flex flex-col justify-between items-center min-h-full')
    Header
    <Nuxt />
    Footer
</template>

<script>
import Header from '../components/Header'
import Footer from '../components/Footer'
export default {
  components: { Header, Footer },
}
</script>

<style></style>
