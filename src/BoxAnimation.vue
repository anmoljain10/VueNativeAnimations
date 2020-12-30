<template>
  <view class="container">
    <view class="box" :style="{transform: [{rotate: '45deg'}]}">
      <view class="flex-row">
        <animated:view
          class="small-box"
          :style="{margin: $options.marginInterpolation}"
        />
        <animated:view
          class="small-box"
          :style="{margin: $options.marginInterpolation}"
        />
      </view>
      <view class="flex-row">
        <animated:view
          class="small-box"
          :style="{margin: $options.marginInterpolation}"
        />
        <animated:view
          class="small-box"
          :style="{margin: $options.marginInterpolation}"
        />
      </view>
    </view>
  </view>
</template>

<script>
import { Animated } from 'react-native'

export default {
    animateMargin:new Animated.Value(0),
    created () {
      this.$options.marginInterpolation = this.$options.animateMargin.interpolate({
        inputRange:[0,0.5,1],
        outputRange:[0,10,0]
      })
    },
    methods:{
      startAnimation () {
        Animated.timing(this.$options.animateMargin,{
          toValue:1,
          duration:1000,
          useNativeDriver:false
        }).start(()=>{
          this.$options.animateMargin.setValue(0)
          this.startAnimation()})
      }
    },
    mounted () {
      this.startAnimation() 
    }
}
</script>

<style scoped>
.flex-row {
  flex-direction: row;
}
.container {
  flex: 1;
  background-color: rgb(201, 76, 77);
  justify-content: center;
  align-items: center;
}
.box {
  position: absolute;
  width: 80;
  height: 80;
  align-items: center;
  justify-content: center;
}
.small-box {
  background-color: white;
  height: 30;
  width: 30;
}
</style>