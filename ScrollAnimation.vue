<template>
  <safe-area-view :style="{flex: 1}">
    <view class="container">
      <animated:image
        :source="lake"
        :style="{
          position: 'absolute',
          zIndex: 1,
          height: animatedSize,
          width: animatedSize,
          borderRadius: animatedSize,
          left: imagePosition,
          top: 50,
        }"
      />
      <animated:view
        :style="{
          backgroundColor: 'rgb(0, 143, 90)',
          flexDirection: 'row',
          width: '100%',
          height: headerHeight,
        }"
      >
      </animated:view>
      <view class="middle-view"> </view>
      <animated:scroll-view
        :on-scroll="
          Animated.event([
            {
              nativeEvent: {
                contentOffset: {
                  y: scrollY,
                },
              },
            },
          ])
        "
        :content-container-style="{paddingLeft: 20, paddingRight: 20}"
      >
        <view>
          <text class="cursive-text" :style="{fontSize: 30}"
            >Incredible India!</text
          >
        </view>
        <view :style="{marginTop: 10}">
          <text
            >The geographic terrain of India is rich and diverse, filled with
            lush green forests, scenic lakes, majestic mountain peaks, mosaics
            of grasslands, tropical beaches, and vast stretches of wilderness.
            From east to west, north to south, this South Asian country packs an
            assortment of treasures for nature lovers. Here is a rundown of some
            of the most beautiful places where you can be at one with nature.
          </text>
        </view>
        <view>
          <text
            >Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            Suspendisse neque odio, pharetra non tincidunt nec, tincidunt nec
            nunc. Etiam sapien neque, faucibus in efficitur at, pharetra id
            nulla. Proin luctus, erat sit amet rutrum tempor, nisl risus blandit
            ligula, ac tincidunt erat mauris sed nisi. Curabitur tempor ultrices
            massa, vitae varius nunc hendrerit a. Vestibulum porttitor sem nunc,
            at lacinia lorem elementum vitae. Sed et metus tempus, suscipit ante
            et, convallis augue. Nulla id malesuada urna, et iaculis dolor.
            Proin sit amet leo eget metus hendrerit placerat quis et enim. Sed
            varius, magna nec accumsan tincidunt, sapien urna sollicitudin
            turpis, vel placerat mi risus a diam. Curabitur magna justo, mollis
            vel semper ac, maximus nec lacus.
          </text>
        </view>
        <view>
          <text
            >Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            Suspendisse neque odio, pharetra non tincidunt nec, tincidunt nec
            nunc. Etiam sapien neque, faucibus in efficitur at, pharetra id
            nulla. Proin luctus, erat sit amet rutrum tempor, nisl risus blandit
            ligula, ac tincidunt erat mauris sed nisi. Curabitur tempor ultrices
            massa, vitae varius nunc hendrerit a. Vestibulum porttitor sem nunc,
            at lacinia lorem elementum vitae. Sed et metus tempus, suscipit ante
            et, convallis augue. Nulla id malesuada urna, et iaculis dolor.
            Proin sit amet leo eget metus hendrerit placerat quis et enim. Sed
            varius, magna nec accumsan tincidunt, sapien urna sollicitudin
            turpis, vel placerat mi risus a diam. Curabitur magna justo, mollis
            vel semper ac, maximus nec lacus.</text
          >
        </view>
        <view>
          <text :style="{fontSize: 15, marginTop: 10}"
            >Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            Suspendisse neque odio, pharetra non tincidunt nec, tincidunt nec
            nunc. Etiam sapien neque, faucibus in efficitur at, pharetra id
            nulla. Proin luctus, erat sit amet rutrum tempor, nisl risus blandit
            ligula, ac tincidunt erat mauris sed nisi. Curabitur tempor ultrices
            massa, vitae varius nunc hendrerit a. Vestibulum porttitor sem nunc,
            at lacinia lorem elementum vitae. Sed et metus tempus, suscipit ante
            et, convallis augue. Nulla id malesuada urna, et iaculis dolor.
            Proin sit amet leo eget metus hendrerit placerat quis et enim. Sed
            varius, magna nec accumsan tincidunt, sapien urna sollicitudin
            turpis, vel placerat mi risus a diam. Curabitur magna justo, mollis
            vel semper ac, maximus nec lacus.</text
          >
        </view>
      </animated:scroll-view>
    </view>
  </safe-area-view>
</template>

<script>
import lake from './assets/lake.jpg'
import { Animated } from 'react-native'

export default {
  data () {
    return {
      Animated,
      lake,
      animatedSize:null,
      imagePosition:null,
      headerHeight:null,
      scrollY:new Animated.Value(0)
    }
  },
  created () {
    this.animatedSize = this.scrollY.interpolate({
      inputRange:[0,100],
      outputRange:[200,100],
      extrapolate:'clamp'
    })
    this.imagePosition = this.scrollY.interpolate({
      inputRange:[0,100],
      outputRange:[100,20],
      extrapolate:'clamp'
    })
    this.headerHeight = this.scrollY.interpolate({
      inputRange:[0,100],
      outputRange:[300,100],
      extrapolate:'clamp'
    })
  },
  computed:{
  }
}
</script>

<style>
.container {
  background-color: white;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
.middle-view {
  height: 50;
}
.cursive-text {
  font-family: arial;
}
</style>
