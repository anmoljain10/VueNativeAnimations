<template>
  <view class="container">
    <animated:view
      v-for="(key, index) in slotNumber"
      :key="index"
      :style="{height: 30}"
    >
      <text class="text-color">{{ key }}</text>
    </animated:view>
    <touchable-opacity :on-press="() => startAnimation()">
      <view class="button">
        <text class="text-color-white">Start Timer</text>
      </view>
    </touchable-opacity>
  </view>
</template>

<script>
import { Animated } from 'react-native'

export default {
    data () {
        return {
            slotNumber:[0,1,2,3,4,5,6,7,8,9],
            offset:-30,
        }
    },
    moveSlot : new Animated.Value(0),
    methods:{
        startAnimation () {
            Animated.timing(this.$options.moveSlot,{
                toValue:9*(this.offset),
                duration:1000,
                useNativeDriver:false
            }).start()
        }
    }
}
</script>

<style>
.container {
  flex: 1;
  justify-content: center;
  align-items: center;
}
.text-color {
  color: #fff;
  font-size: 25;
}
.button {
  padding: 10;
  background-color: #ff5733;
}
.text-color-white {
  color: white;
  font-size: 20;
}
.text {
  font-family: arial;
  margin: 10;
}
</style>