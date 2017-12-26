<template>
  <div class="part_5">
    <div class="content">
      <transition name="slide-down">
        <div class="title"  v-if="show">{{data.title}}</div>
      </transition>
      <transition name="slide-up">
        <div class="info"  v-if="show">{{data.info}}</div>
      </transition>
    </div>
    <transition name="scale">
      <div class="pictrue" v-if="show"></div>
    </transition>
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
      show: false
    }
  },
  methods: {
    scroll () {
      this.scrollHeight = document.documentElement.scrollTop || document.body.scrollTop
      if (this.scrollHeight > 2399) {
        this.show = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.scroll)
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.part_5
    position: absolute
    background: #d9dde1
    .content
      position: absolute
      width:100%
      top: 150px
      text-align: center
      .title
        font-size: 42px
        color: #f01414
        margin-bottom: 28px
    .pictrue
      position: absolute
      bottom:-100px
      width: 100%
      height: 370px
      background: url('bg-screen-5.png') no-repeat
      background-size:1737px 370px
      background-position: center
  .slide-up-enter-active, .slide-down-enter-active,.scale-enter-active
    transition: all 1s
  .slide-up-enter
    opacity: 0
    transform: translate(0,100%)
  .slide-down-enter
    opacity: 0
    transform: translate(0,-100%)
  .scale-enter
    transform: scale(0.5)
</style>