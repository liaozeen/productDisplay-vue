<template>
  <div class="part_2">
    <div class="content">
      <transition name="slide-down">
        <span class="title" v-if="show">{{data.title}}</span>
      </transition>
      <transition name="slide-up">
        <span class="info"  v-if="show">{{data.info[0]}}</span>
        <span class="info"  v-if="show">{{data.info[1]}}</span>
      </transition>
    </div>
    <transition name="slide-up">
      <div class="phone" v-if="show"></div>
    </transition>
    <div class="points">
      <transition name="point_1">
        <div class="point_1 point" v-if="show">{{data.mark[0]}}</div>
      </transition>
      <transition name="point_2">
        <div class="point_2 point" v-if="show">{{data.mark[1]}}</div>
      </transition>
      <transition name="point_3">
        <div class="point_3 point" v-if="show">{{data.mark[2]}}</div>
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
      show: false
    }
  },
  methods: {
    scroll () {
      this.scrollHeight = document.documentElement.scrollTop || document.body.scrollTop
      if (this.scrollHeight > 599) {
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
.part_2
  color: rgb(7,17,27)
  background-color: #fafafa
  .content
    position: absolute
    width: 100%
    top: 100px
    text-align: center
    .title
      display: block
      font-size: 42px
      font-weight: normal
      color: #f01414
      margin-bottom: 20px
    .info
      display: block
      line-height: 20px
  .phone,.points
    position: absolute
    left: 50%
    margin-left: -464px
    top: 290px
  .phone
    width: 800px
    height: 873px
    background: url("bg-screen-2.png") no-repeat
  .points
    .point
      font-size: 24px
      color: #4D555d
      position: absolute
      width: 100px
      &:before,&:after
        content: ' '
        display: block
        width: 20px
        height: 20px
        position: absolute
        background: rgba(255,0,0,0.4)
        border-radius: 50%
        margin: 2px 0
        animation: bounce 2s infinite
      &:before
        animation:  bounce 2s infinite 1s
      &:after
        top: 0
    .point_1
      top: 180px
      left: -120px
      padding-right: 112px
      background: url("icon-point-right.png") no-repeat center right
      &.point:before,&.point:after
        right: 0
    .point_2
      top: 37px
      left: 584px
      padding-left: 112px
      background: url("icon-point-left.png") no-repeat center left
      &.point:before,&.point:after
        left: 0
    .point_3
      top: 300px;
      left: 660px;
      padding-left: 112px
      background: url("icon-point-left.png") no-repeat center left
      &.point:before,&.point:after
        left: 0
    .slide-up-enter-active, .slide-down-enter-active
      transition: all 1s
    .slide-up-enter
      opacity: 0
      transform: translate(0,100%)
    .slide-down-enter
      opacity: 0
      transform: translate(0,-100%)
    .point_1-enter-active
      transition: all 1s .5s
    .point_2-enter-active
      transition: all 1s 1s
    .point_3-enter-active
      transition: all 1s 1.3s
    .point_1-enter
      transform: translateX(-500px)
    .point_2-enter,.point_3-enter
      transform: translateX(500px)
    @-webkit-keyframes bounce
      0%,100%{
      transform: scale(0.3);
      }
      50%{
      transform: scale(1);
      }
</style>