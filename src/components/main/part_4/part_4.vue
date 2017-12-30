<template>
  <div class="part_4">
    <div class="content">
      <transition name="slide-down">
        <div class="title" v-if="show">{{data.title}}</div>
      </transition>
      <transition name="slide-up">
        <div class="info" v-if="show">{{data.info}}</div>
      </transition>
    </div>
    <div class="phone_list">
      <transition name="item_1">
        <div class="phone_item phone_item_1"  v-if="show">
          <div class="phone_style">{{data.color[0]}}</div>
          <div class="size_info">{{data.size_info}}</div>
        </div>
      </transition>
      <transition name="item_2">
        <div class="phone_item phone_item_2"  v-if="show">
          <div class="phone_style">{{data.color[1]}}</div>
          <div class="size_info">{{data.size_info}}</div>
        </div>
      </transition>
      <transition name="item_3">
        <div class="phone_item phone_item_3"  v-if="show">
          <div class="phone_style">{{data.color[2]}}</div>
          <div class="size_info">{{data.size_info}}</div>
        </div>
      </transition>
      <transition name="item_4">
        <div class="phone_item phone_item_4"  v-if="show">
          <div class="phone_style">{{data.color[3]}}</div>
          <div class="size_info">{{data.size_info}}</div>
        </div>
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
      if (this.scrollHeight > 1799) {
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
.part_4
  position: absolute
  .content
    position: absolute
    width: 100%
    top: 80px
    text-align:center
    .title
      font-size: 42px
      color: #f01414
      margin-bottom: 28px
  .phone_list
    display: flex
    position:absolute
    width:1200px
    height: 320px
    left: 50%
    margin-left:-600px
    top: 240px
    .phone_item
      position:relative
      flex:1
      .phone_style,.size_info
        position:absolute
        width: 100%
        text-align: center
      .phone_style
        bottom:20px
        color: #2c3238
      .size_info
        font-size: 9px
        bottom:0
        color: #93999f
    .phone_item_1
      background:url('./phone-1.png')
    .phone_item_2
      background:url('./phone-2.png')
    .phone_item_3
      background:url('./phone-3.png')
    .phone_item_4
      background:url('./phone-4.png')
    .phone_item_1,.phone_item_2,.phone_item_3,.phone_item_4
      background-repeat:no-repeat
      background-position: center top
  .slide-up-enter-active, .slide-down-enter-active
    transition: all 1s
  .slide-up-enter,.item_1-enter,.item_2-enter,.item_3-enter,.item_4-enter
    opacity: 0
    transform: translate(0,100%)
  .slide-down-enter
    opacity: 0
    transform: translate(0,-100%)
  .item_1-enter-active
    transition: all 1s 0.5s
  .item_2-enter-active
    transition: all 1s 1s
  .item_3-enter-active
    transition: all 1s 1.5s
  .item_4-enter-active
    transition: all 1s 2s
</style>