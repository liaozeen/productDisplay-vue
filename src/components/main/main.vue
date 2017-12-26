<template>
  <div class="main">
    <partOne id="part_1" class="part" :data="detail[0]"></partOne>
    <partTwo  id="part_2" class="part" :data="detail[1]"></partTwo>
    <partThree id="part_3" class="part" :data="detail[2]"></partThree>
    <partFour id="part_4" class="part" :data="detail[3]"></partFour>
    <partFive id="part_5" class="part" :data="detail[4]"></partFive>
    <partSix @to-show="toShow"></partSix>
  </div>
</template>

<script type="text/ecmascript-6">
import partOne from './part_1/part_1.vue'
import partTwo from './part_2/part_2.vue'
import partThree from './part_3/part_3.vue'
import partFour from './part_4/part_4.vue'
import partFive from './part_5/part_5.vue'
import partSix from './part_6/part_6.vue'

export default {
  props: {
    data: {
      type: Object
    },
    detail: {
      type: [Object, Array]
    }
  },
  methods: {
    toShow () {
      this.$emit('to-show')
    }
  },
  components: {
    partOne,
    partTwo,
    partThree,
    partFour,
    partFive,
    partSix
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.main
  position: relative
  width: 100%
  .part
    position: relative
    height: 660px
    width 100%
    overflow: hidden
</style>