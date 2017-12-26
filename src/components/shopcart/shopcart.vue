<template>
<div class="shopcart">
  <div class="shopcart_main">
    <div class="shopcart_top">
      <div class="top_title">选择手机型号</div>
      <div class="top_close" @click="closeCart">&times;</div>
    </div>
    <div class="shopcart_center">
      <div class="center_pictrue" :class="imageUrl"></div>
      <div class="center_features">
        <div class="features_list">
          <div class="list_title">机身颜色</div>
          <ul class="lists">
            <li>
              <input type="radio" name="color" id="color1" class="input_radio" value="color_0"  @click="checked">
              <label for="color1" :class="{radio_color:true, checked: colors[0]}" >{{data.color[0]}}</label>
            </li>
            <li>
              <input type="radio" name="color" id="color2" class="input_radio" value="color_1"  @click="checked">
              <label for="color2" :class="{radio_color:true, checked: colors[1]}">{{data.color[1]}}</label>
            </li>
            <li>
              <input type="radio" name="color" id="color3" class="input_radio" value="color_2"  @click="checked">
              <label for="color3" :class="{radio_color:true, checked: colors[2]}">{{data.color[2]}}</label>
            </li>
            <li>
              <input type="radio" name="color" id="color4" class="input_radio" value="color_3"  @click="checked">
              <label for="color4" :class="{radio_color:true, checked: colors[3]}">{{data.color[3]}}</label>
            </li>
          </ul>
        </div>
        <div class="features_list">
          <div class="list_title">空间容量</div>
          <ul class="lists">
            <li>
              <input type="radio" name="size" id="size1" class="input_radio" value="size_0"  @click="checked">
              <label for="size1" :class="{radio_size:true, checked: sizes[0]}">{{data.style[0].size}}</label>
            </li>
            <li>
              <input type="radio" name="size" id="size2" class="input_radio" value="size_1"  @click="checked">
              <label for="size2"  :class="{radio_size:true, checked: sizes[1]}">{{data.style[1].size}}</label>
            </li>
            <li>
              <input type="radio" name="size" id="size3" class="input_radio" value="size_2"  @click="checked">
              <label for="size3"  :class="{radio_size:true, checked: sizes[2]}">{{data.style[2].size}}</label>
            </li>
          </ul>
        </div>
        <div class="features_list">
          <div class="list_title">购买数量</div>
          <div class="pay_num">
            <input type="text" class="pay_amount" value="1" v-model="number">
            <div class="pay_minus" @click="decrease">&or;</div>
            <div class="pay_add" @click="add">&and;</div>
          </div>
        </div>
      </div>
    </div>
    <div class="shopcart_footer">
      <span class="selected">已选择："{{selected}}","{{size}}",x{{number}}</span>
      <span class="clearance" @click="pay">去结算</span>    
      <span class="rate">&yen; {{totalPrice}}</span>
    </div>
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
      imageUrl: 'phone_1',
      color: '中国红',
      price: 999,
      size: '16G',
      number: 1
    }
  },
  created () {
    this.colors = [true, false, false, false]
    this.sizes = [true, false, false]
    this.classMap = ['phone_1', 'phone_2', 'phone_3', 'phone_4']
  },
  computed: {
    selected () {
      return this.color
    },
    totalPrice () {
      return this.price * this.number
    }
  },
  methods: {
    closeCart () {
      this.$emit('to-close')
    },
    add () {
      this.number ++
    },
    decrease () {
      if (this.number > 1) {
        this.number --
      }
    },
    pay () {
      alert(`商品购物成功！
        您一共购买了${this.number} 部${this.color}，${this.size} 摩亚手机，
        实际付款：${this.totalPrice}元
      `)
      this.closeCart()
      // 重置数据
      this.number = 1
      this.color = this.data.color[0]
      this.size = this.data.style[0].size
      this.colors = [true, false, false, false]
      this.sizes = [true, false, false]
    },
    checked (e) {
      let value = e.target.value
      switch (value) {
        case 'color_0':
          this.colors = [true, false, false, false]
          this.imageUrl = this.classMap[0]
          this.color = this.data.color[0]
          break
        case 'color_1':
          this.colors = [false, true, false, false]
          this.imageUrl = this.classMap[1]
          this.color = this.data.color[1]
          break
        case 'color_2':
          this.colors = [false, false, true, false]
          this.imageUrl = this.classMap[2]
          this.color = this.data.color[2]
          break
        case 'color_3':
          this.colors = [false, false, false, true]
          this.imageUrl = this.classMap[3]
          this.color = this.data.color[3]
          break
        case 'size_0':
          this.sizes = [true, false, false]
          this.size = this.data.style[0].size
          this.price = this.data.style[0].price
          break
        case 'size_1':
          this.sizes = [false, true, false]
          this.size = this.data.style[1].size
          this.price = this.data.style[1].price
          break
        case 'size_2':
          this.sizes = [false, false, true]
          this.size = this.data.style[2].size
          this.price = this.data.style[2].price
          break
      }
    }
  }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
.shopcart
    position: fixed
    width: 100%
    height: 100%
    left: 0
    top: 0
    background: rgba(0, 0, 0,0.4)
    z-index: 9998
    .shopcart_main
        position: fixed
        left: 50%
        margin-left: -300px
        top: 50%
        margin-top: -200px
        width: 600px
        height: 320px
        border-radius: 5px
        background: #fff
        box-shadow: 0px 0px 12px 4px rgba(65, 138, 212, 0.8)
        .shopcart_top
            position: absolute
            width: 100%
            height: 30px
            top: 0
            left: 0
            background: rgb(243,243,243)
            .top_title
                position: absolute
                height: 30px
                left: 8px
                line-height: 30px
                font-size: 14px
                color: rgb(102,102,102)
            .top_close
                position: absolute
                width: 30px
                height: 30px
                right: 0
                line-height: 30px
                font-size: 18px
                font-weight: 700
                text-align: center
                color: rgb(205,205,205)
                cursor: pointer
                &:hover
                    color: rgb(224, 13, 13)
        .shopcart_center
            position: absolute
            width: 100%
            height: 220px
            top: 30px
            .center_pictrue
                position: absolute
                width: 140px
                height: 180px
                left: 30px
                padding: 8px
                margin-top: 10px
                border: solid 1px rgb(206, 200, 200)
                border-radius: 5px
                background-size: 140px 180px
                background-repeat: no-repeat
                background-position: center 
                &.phone_1
                  background-image: url('../main/part_4/phone-1.png')
                &.phone_2
                  background-image: url('../main/part_4/phone-2.png')
                &.phone_3
                  background-image: url('../main/part_4/phone-3.png')
                &.phone_4
                  background-image: url('../main/part_4/phone-4.png')
            .center_features
                position: absolute
                width: 400px
                left: 208px
                margin-top: 10px
                .features_list
                    width: 100%
                    height: 58px
                    margin: 4px 0 0 0
                    font-size: 14px
                    .list_title
                        display: block
                        color: #838383
                        font-family: tahoma,arial,sans-serif
                        margin-bottom: 4px
                    .lists
                        list-style: none
                        margin: 0
                        padding: 0
                        color: #666
                        font-family: tahoma,arial,sans-serif
                        .input_radio
                            display: none
                        .radio_size,.radio_color
                            float: left
                            width: 68px
                            height: 30px
                            text-align: center
                            line-height: 30px
                            border: 1px solid #b8b7bd
                            margin-right: 4px
                            cursor: pointer
                        .radio_size:hover,.radio_color:hover
                            border: 2px solid #FF0036
                            margin: -1px 3px -1px -1px
                        .checked
                            border: 2px solid #FF0036
                            background: #FF0036
                            color: #fff
                            margin: -1px 3px -1px -1px
                    .pay_num
                        position: absolute
                        width: 56px
                        height:36px
                    .pay_amount
                        position: absolute
                        width: 30px
                        height: 34px
                        border: 1px solid #93999f  
                    .pay_add,.pay_minus
                        position: absolute
                        width: 15px
                        height: 14px
                        right: 0
                        text-align: center
                        line-height: 14px
                        border: solid 1px #93999f
                        cursor: pointer
                        &:active
                            background:#93999f
                            color: #fff
                    .pay_add
                        top: 0
                    .pay_minus
                        bottom: 0
        .shopcart_footer
            position: absolute
            width: 100%
            height: 60px
            left: 0
            top:240px
            margin-top: 10px
            border-top: solid 1px #93999f
            .selected
                position: absolute
                height: 36px
                color: #838383
                font-size: 14px
                line-height: 36px
                left: 30px
                top: 12px
            .rate,.clearance
                float: right
                line-height: 36px
                height: 36px
                margin-top: 12px
            .rate
                font-size: 18px
                font-weight: 700
                color: rgb(228,61,64)
                right: 150px
                margin-right: 10px
            .clearance
                right: 20px
                width: 100px
                text-align: center
                color: #fff
                background: rgb(228,61,64)
                border-radius: 3px
                cursor: pointer
                margin-right: 30px
</style>
