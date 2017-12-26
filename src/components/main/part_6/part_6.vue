<template>
  <div class="part_6">
    <div class="part_6_buy" @click="buy">立即购买</div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  methods: {
    buy () {
      this.$emit('to-show')
    }
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.part_6
    position: relative
    width: 100%
    height: 300px
    background: url('bg-screen-buy.png') center
    .part_6_buy
      position: absolute
      width: 240px
      height: 80px
      color: #fff
      background: #f01414
      font-size: 24px
      text-align: center
      line-height: 80px
      border-radius: 3px
      cursor: pointer
      top: 50%
      left: 50%
      margin-top: -40px
      margin-left: -120px
</style>