<template>
  <safe-area-view :style="{flex: 1, backgroundColor: 'rgb(39, 40, 34)'}">
    <!-- Uncomment one to see -->
    <!-- <box-animation /> -->
    <slot-animation />
    <!-- <scroll-animation /> -->
    <!-- <hexagon /> -->
    <!-- <progress-loader /> -->
    <!-- <vue-native-anim /> -->
    <!-- <example /> -->
  </safe-area-view>
</template>

<script>
import BoxAnimation from './BoxAnimation'
import { ImageBackground } from 'react-native'
import ScrollAnimation from './ScrollAnimation'
import SlotAnimation from './SlotAnimation'
import Game from './game.jpg'
import ProgressLoader from './ProgressLoader.vue'
import Hexagon from './Hexagon'
import VueNativeAnim from './VueNativeAnim'
import Example from './Example'

export default {
  data () {
    return {
        Game
        }
  },
  components:{
    Hexagon,
    BoxAnimation,
    ScrollAnimation,
    SlotAnimation,
    ImageBackground,
    ProgressLoader,
    VueNativeAnim,
    Example
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
