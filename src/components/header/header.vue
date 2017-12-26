<template>
  <div :class="{ header:true, header_color: isChange}">
    <div class="header_left">
      <img src="./logo.png">
      <div class="name">{{data.name}}</div>
    </div>
    <div class="header_right">
      <ul class="nav_top">
        <li ><a href="#part_1" :class="{ nav_top_item:true, active: isActive[0], nav_color:isChange}">外观</a></li>
        <li ><a href="#part_2" :class="{ nav_top_item:true, active: isActive[1], nav_color:isChange}">说明</a></li>
        <li ><a href="#part_3" :class="{ nav_top_item:true, active: isActive[2], nav_color:isChange}">配置</a></li>
        <li ><a href="#part_4" :class="{ nav_top_item:true, active: isActive[3], nav_color:isChange}">型号</a></li>
        <li ><a href="#part_5" :class="{ nav_top_item:true, active: isActive[4], nav_color:isChange}">其他</a></li>
      </ul>
      <div class="header_buy" @click="buy">立即购买</div>
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
      isActive: [true, false, false, false, false],
      isChange: false
    }
  },
  methods: {
    scroll () {
      this.scrollHeight = document.documentElement.scrollTop || document.body.scrollTop
      this.isActive = [false, false, false, false, false]
      if (this.scrollHeight > 0) {
        this.isChange = true
      } else {
        this.isChange = false
      }
      if (this.scrollHeight > -1 && this.scrollHeight < 600) {
        this.isActive[0] = true
      }
      if (this.scrollHeight > 599 && this.scrollHeight < 1200) {
        this.isActive[1] = true
      }
      if (this.scrollHeight > 1199 && this.scrollHeight < 1800) {
        this.isActive[2] = true
      }
      if (this.scrollHeight > 1799 && this.scrollHeight < 2400) {
        this.isActive[3] = true
      }
      if (this.scrollHeight > 2399) {
        this.isActive[4] = true
      }
    },
    buy () {
      this.$emit('to-show')
    }
  },
  mounted () {
    window.addEventListener('scroll', this.scroll)
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.header
  position: fixed
  left: 0
  top: 0
  width: 100%
  height: 60px
  background: #FAFAFA
  transition: all 1s
  z-index: 999
  .header_left
    position: absolute
    width: 100%
    left: 10px
    top: 10px
    .name
      position: absolute
      left: 50px
      top: 10px
      font-size: 18px
  .header_right
    display:flex
    position: absolute
    right: 10px
    top: 10px
    .nav_top
      display:flex
      flex:1
      .nav_top_item
        flex:1
        display: inline-block
        width: 50px
        padding: 10px 0
        margin: 0 25px
        text-align: center
        text-decoration: none
        font-size: 14px
        &:hover
          color: red
          border-bottom: 2px solid red
      .active
        color: red
        border-bottom: 2px solid red
    .header_buy
      width: 100px
      height 14px
      padding: 10px 0
      text-align: center
      font-size: 14px
      color:#fff
      background: black
      border-radius: 5px
      cursor: pointer
.header_color
  background: rgba(0,0,0,.5)
  color: #fff
.nav_color
  color: #fff
</style>
