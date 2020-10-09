<template lang="pug">
  li(class='py-4 mb-3 flex justify-center items-center w-3/12 sm:w-1/12')
    .tooltip-box
      img(class='w-4/5 h-4/5 object-contain img-tooltip relative opacity-50' :src="icon.path" :alt='icon.alt' @mouseover="hover = true" @mouseleave="hover = false" :class="hover ? 'opacity-100' : 'opacity-50'" @click="verTooltip")
      .tooltip(v-show="hover")
        span.triangle
        | {{ icon.alt }}
</template>

<script>
export default {
  name: 'Tooltip',
  props: {
    icon: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      hover: false,
    }
  },
  methods: {
    verTooltip() {
      this.hover = true
      setTimeout(() => {
        this.hover = false
      }, 850)
    },
  },
}
</script>

<style lang="css" scoped>
.tooltip {
  background: #95088d;
  color: #ffffff;
  text-align: center;
  padding: 5px 10px 5px 10px;
  border-radius: 10px;
  top: calc(100% + 11px);
  left: 50%;
  transform: translate-x(-50%);
}
.triangle {
  border-width: 0 6px 6px;
  border-color: transparent;
  border-bottom-color: #97266d;
  position: absolute;
  top: -6px;
  left: 50%;
  transform: translate-x(-50%);
}
</style>
