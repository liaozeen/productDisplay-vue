<template>
  <ul class="nav_side">
    <li ><a href="#part_1" class="nav_item" :class="{ active: isActive[0] }">外观</a></li>
    <li ><a href="#part_2" class="nav_item" :class="{ active: isActive[1] }">说明</a></li>
    <li ><a href="#part_3" class="nav_item" :class="{ active: isActive[2] }">配置</a></li>
    <li ><a href="#part_4" class="nav_item" :class="{ active: isActive[3] }">型号</a></li>
    <li ><a href="#part_5" class="nav_item" :class="{ active: isActive[4] }">其他</a></li>
  </ul>
</template>

<script type="text/ecmascript-6">
export default {
  data () {
    return {
      isActive: [true, false, false, false, false]
    }
  },
  methods: {
    scroll () {
      this.scrollHeight = document.documentElement.scrollTop || document.body.scrollTop
      this.isActive = [false, false, false, false, false]
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
    }
  },
  mounted () {
    window.addEventListener('scroll', this.scroll)
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.nav_side
    position: fixed
    right: 0
    top: 50%
    margin-top: -119.5px
    width: 60px
    height: 239px
    font-size: 12px
    background: #fff
    box-shadow: 0px 4px 12px 0px rgba(7, 17, 27, 0.1)
    .nav_item
        display: block
        width: 40px
        height: 30px
        line-height: 30px
        text-decoration: none
        text-align: center
        padding: 5px 0
        color: #93999f
        border-top: 1px solid #eee
        margin: 5px 10px 0 10px
        &:first-child
          border: none
          margin-top: 7.5px
        &:hover   
            color: red
    .active
      color: red
</style>
