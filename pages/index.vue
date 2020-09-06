<template lang="pug">
  div.w-full.flex.flex-col.justify-between.content-center.min-h-full
    Header
    Home
    Footer
</template>

<script>
import Header from '../components/Header'
import Footer from '../components/Footer'
import Home from '../components/Home'
export default {
  components: { Header, Footer, Home },
}
</script>

<style></style>
