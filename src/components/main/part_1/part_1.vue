<template>
  <div class="part_1">
   <div class="bg_one"></div>
   <transition name="slide-up">
    <div class="content" v-if="show">
        <span class="title">{{data.title}}</span>
        <span class="info">{{data.info}}</span>
    </div>
   </transition>
   <div class="pictrue">
      <transition name="slide-down">
        <div class="phone" v-if="show"></div>
      </transition>
      <transition name="slide-up">
        <div class="shadow"  v-if="show"></div>
      </transition>
   </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    data: {
      type: Object
    }
  },
  data () {
    return {
      show: false,
      scrollHeight: 0
    }
  },
  methods: {
    /*
    scroll () {
      this.scrollHeight = document.documentElement.scrollTop
    }
    */
  },
  mounted () {
   // window.addEventListener('scroll', this.scroll)
    this.show = true
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.part_1
  .bg_one
    position: absolute
    width:  100%
    height: 100%
    background-image: url("bg-screen-1.png")
    background-size: 100% 100%
    z-index: -999
  .content
    position: absolute
    text-align: center
    top: 130px
    left: 0
    right: 0
    margin: 0 auto
    font-size: 42px
    font-weight: normal
    .title
      color: #f01414
    .info
      color:#fff
  .pictrue
    position: absolute
    width: 1000px
    height: 333px
    top: 300px
    left: 50%
    margin-left: -500px
    .phone,.shadow
      position: absolute
      width: 1000px
      height: 100%
      background-repeat: no-repeat
    .phone
      background-image: url("screen-1-phone.png")
      background-size: 1000px 222px
      z-index: 2
    .shadow
      background-image: url("screen-1-shadow.png")
      background-size: 1000px 333px
      z-index: 1
  .slide-up-enter-active, .slide-down-enter-active
    transition: all 1s
  .slide-up-enter
    opacity: 0
    transform: translate(0,100%)
  .slide-down-enter
    opacity: 0
    transform: translate(0,-100%)
</style>