<template>
  <safe-area-view :style="{flex: 1}">
    <!-- Uncomment one to see -->
    <box-animation />
    <!-- <slot-animation /> -->
    <!-- <scroll-animation /> -->
  </safe-area-view>
</template>

<script>
import BoxAnimation from './BoxAnimation'
import ScrollAnimation from './ScrollAnimation'
import SlotAnimation from './SlotAnimation'

export default {
  components:{
    BoxAnimation,
    ScrollAnimation,
    SlotAnimation
  }
}
</script>

<style>
.container {
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>
