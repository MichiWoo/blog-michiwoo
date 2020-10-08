<template lang="pug">
  div
    img(:src='icon.path' :alt='icon.alt' widt='50' heigth='50')
</template>

<script>
export default {
  name: 'Icon',
  props: {
    icon: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style lang="scss" scoped></style>
