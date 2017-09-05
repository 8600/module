<template lang="pug">
  .control-entry
    span.control-text {{name}}
    .input-box.number-entry(v-if="typeof(value) == 'number'")
      .less.bottom(@click="less") －
      input(type="number", v-bind:value="value", v-on:input="updateValue($event.target.value)")
      .more.bottom(@click="more") ＋
    .input-box(v-if="typeof(value) == 'string'")
      input.control-input(type="text", v-bind:value="value", v-on:input="updateValue($event.target.value)")
</template>

<script>
  import { Order } from '../../../../Order.js'
  export default {
    props: {
      value: null,
      max: Number,
      min: Number,
      name: String,
      fun: Function
    },
    methods: {
      updateValue: function (data) {
        let newData = null
        if (typeof (this.value) === 'number') {
          let newData = parseInt(data)
          if (this.max && this.max <= newData) newData = this.max
          if (this.min && this.min >= newData) newData = this.min
        } else {
          newData = data
        }
        this.$emit('input', newData)
        if (this.fun) this.fun()
        Order.$emit('needUpdata')
      },
      less: function () {
        let newData = this.value - 1
        if (this.max && this.max <= newData) newData = this.max
        if (this.min && this.min >= newData) newData = this.min
        this.$emit('input', newData)
        if (this.fun) this.fun()
        Order.$emit('needUpdata')
      },
      more: function () {
        let newData = this.value + 1
        if (this.max && this.max <= newData) newData = this.max
        if (this.min && this.min >= newData) newData = this.min
        this.$emit('input', newData)
        if (this.fun) this.fun()
        Order.$emit('needUpdata')
      }
    }
  }
</script>

<style lang='less' scoped>
.number-entry input {
  width: 60px;
  text-align: center;
  border: none;
  color: mintcream;
  background-color: darkgrey;
}
.input-box {
  display: flex;
  border-radius: 5px;
  overflow: hidden;
  color: white;
  .bottom {
    text-align: center;
    line-height: 25px;
    width: 20px;
    background-color: dimgray;
    font-size: 20px;
    cursor: pointer;
    user-select: none;
  }
  .bottom:hover {
    background-color: deepskyblue;
    color: antiquewhite;
  }
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button{
  -webkit-appearance: none !important;
  margin: 0; 
}
</style>
