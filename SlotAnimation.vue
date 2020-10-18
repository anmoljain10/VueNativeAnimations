<template>
  <view class="container">
    <view :style="{height: 30, overflow: 'hidden', margin: 10}">
      <animated:view
        v-for="(key, index) in slotNumber"
        :key="index"
        :style="{height: 30, transform: [{translateY: moveSlot}]}"
      >
        <text class="text-color">{{ key }}</text>
      </animated:view>
    </view>
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
            moveSlot:null,
            slotNumber:[0,1,2,3,4,5,6,7,8,9],
            offset:-30,
        }
    },
    created () {
        this.moveSlot = new Animated.Value(0)
    },
    methods:{
        startAnimation () {
            Animated.timing(this.moveSlot,{
                toValue:9*(this.offset),
                duration:1000
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
  color: #ff5733;
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