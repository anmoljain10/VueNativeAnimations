<template>
  <safe-area-view :style="{flex: 1, backgroundColor: 'rgb(39, 40, 34)'}">
    <!-- Uncomment one to see -->
    <!-- <box-animation /> -->
    <slot-animation />
    <!-- <scroll-animation /> -->
    <!-- <progress-loader /> -->
  </safe-area-view>
</template>

<script>
import BoxAnimation from './src/BoxAnimation'
import { ImageBackground } from 'react-native'
import ScrollAnimation from './src/ScrollAnimation'
import SlotAnimation from './src/SlotAnimation'
import ProgressLoader from './src/ProgressLoader.vue'

export default {
  components:{
    BoxAnimation,
    ScrollAnimation,
    SlotAnimation,
    ImageBackground,
    ProgressLoader,
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
