<template>
  <div class="part_3">
    <div class="content">
      <transition name="slide-down">
        <div class="title" v-if="show">{{data.title}}</div>
      </transition>
      <transition name="slide-up">
        <div class="info" v-if="show">{{data.info[0]}}</div>
      </transition>
      <transition name="slide-up">
        <div class="info" v-if="show">{{data.info[1]}}</div>
      </transition>
    </div>
    <transition name="scale">
      <div class="features" v-if="show">
        <div class="features_item">
          <span class="features_item_number number_1">{{data.features[0].number}}</span>
          <span class="features_item_info">{{data.features[0].info}}</span>
        </div>
        <div class="features_item">
          <span class="features_item_number number_2">{{data.features[1].number}}</span>
          <span class="features_item_info">{{data.features[1].info}}</span>
        </div>
        <div class="features_item">
          <span class="features_item_number number_3">{{data.features[2].number}}</span>
          <span class="features_item_info">{{data.features[2].info}}</span>
        </div>
          <div class="features_item">
          <span class="features_item_number number_4">{{data.features[3].number}}</span>
          <span class="features_item_info">{{data.features[3].info}}</span>
        </div>
      </div>
    </transition>
    <transition name="slide-up">
      <div class="phone" v-if="show"></div>
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
      if (this.scrollHeight > 1199) {
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
@keyframes swing
  0%{ transform:rotate(0deg) }
  10%{ transform:rotate(3deg) }
  20%{ transform:rotate(-3deg) }
  30%{ transform:rotate(2deg) }
  40%{ transform:rotate(-2deg) }
  50%{ transform:rotate(1deg) }
  60%{ transform:rotate(-1deg) }
  70%{ transform:rotate(0deg) }
  100%{ transform:rotate(0deg) }
.part_3
    color: #fff
    background: #a71316
    .content
      position: absolute
      width: 580px
      top: 110px
      left: 100px
      .title
        display: block
        font-size: 36px
        margin-bottom: 36px
      .info
        line-height: 20px
    .features
      position: absolute
      width: 328px
      height: 288px
      top: 310px
      left: 100px
      transform: scale(1)
      .features_item
        position: relative
        float: left
        width: 138px
        height: 118px
        color: #fff
        border: 1px solid #D97173
        margin: 0 24px 24px 0
        border-radius: 3px
        text-align: center
        cursor: pointer
        transition: all 0.5s
        &:hover
          transform: scale(1.05)
        .features_item_number,.features_item_info
          position: absolute
          display: block
          width: 100%
        .features_item_number
          font-size: 36px
          line-height:36px
          top: 31px
        .features_item_info
          top:71px
        .number_1
          -webkit-animation: swing 2s infinite ease-in-out .5s
        .number_2
          -webkit-animation: swing 2s infinite ease-in-out .8s
        .number_3
          -webkit-animation: swing 2s infinite ease-in-out 1.3s
        .number_4
          -webkit-animation: swing 2s infinite ease-in-out 1.5s
    .phone
      position: absolute
      width: 500px
      height: 618px
      right: 100px
      top:160px
      background: url("./bg-screen-3.png") no-repeat
      background-size: 500px 618px
.slide-up-enter-active, .slide-down-enter-active,.scale-enter-active
  transition: all 1s
.slide-up-enter
  opacity: 0
  transform: translate(0,100%)
.slide-down-enter
  opacity: 0
  transform: translate(0,-100%)
.scale-enter
  -webkit-transform: scale(0)
</style>