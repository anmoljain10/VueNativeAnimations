<template>
  <safe-area-view :style="{flex: 1}">
    <view class="container">
      <view class="loading">
        <text class="loading-text">Loading...</text>
      </view>
      <view class="justify-center">
        <view class="progressBar">
          <animated:view
            class="absolute-fill"
            :style="{
              width: $options.loaderWidth,
            }"
          />
        </view>
      </view>
    </view>
  </safe-area-view>
</template>

<script>
import { Animated, Platform } from 'react-native'

export default {
  data () {
    return {
      progressValue:0,
    }
  },
  progress:new Animated.Value(0),
  created: function () {
    this.$options.loaderWidth = this.$options.progress.interpolate({
      inputRange: [0, 100],
      outputRange: ['0%', '100%'],
      extrapolate: 'clamp',
    })
  },
  mounted () {
    this.startAnimation ()
  },
  watch: {
    progressValue: function () {
      Animated.timing(this.$options.progress, {
        toValue: this.progressValue,
        duration: 1000,
        useNativeDriver: false,
      }).start()
    },
  },
  methods:{
    startAnimation() {
      setTimeout(()=>{
      this.loaderWidthTimer = setInterval(()=>{
        if(this.progressValue >= 100) {
          clearInterval(this.loaderWidthTimer)
        }
        this.progressValue = this.progressValue + 10
      },200)
      },10000)
    }
  }
}
</script>

<style>
.container {
  flex: 1;
  justify-content: center;
}
.white-text {
  color: white;
  font-family: Proxima Nova;
  font-style: normal;
  font-weight: bold;
  font-size: 20;
  line-height: 63;
}
.loading {
  align-items: center;
}
.loading-text {
  font-family: ChalkboardSE-Bold;
  color: #fff;
  margin-bottom: 15;
  font-size: 30;
}
.progressBar {
  height: 20;
  width: 80%;
  background-color: rgba(0, 0, 0, 0.5);
  border-radius: 50px;
}
.absolute-fill {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: rgb(1, 142, 67);
  border-radius: 50;
}
.justify-center {
  align-items: center;
  justify-content: center;
}
</style>
