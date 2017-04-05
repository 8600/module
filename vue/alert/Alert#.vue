<template lang="pug">
.alert-box(v-show="show")
  .main-box
    .text-box
      p {{title}}
      .text {{text}}
    .button(v-on:click="close") 确定
</template>

<script>
export default {
  props: {
    title: String,
    text: String
  },
  data () {
    return {
      show: false
    }
  },
  methods: {
    close:function () {
      this.show = false
    }
  },
}
</script>

<style scoped>
.alert-box {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    background-color: rgba(0, 0, 0, 0.5);
}
.main-box {
    position: absolute;
    height: 150px;
    background-color: white;
    border: 1px solid gray;
    border-radius: 5px;
    padding: 10px;
    width: 80%;
    margin: auto;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}
.text-box p {
    height: 40px;
    line-height: 40px;
    text-align: center;
    font-size: 1.2rem;
}
.text-box .text {
    text-align: center;
    color: #999;
    height: 70px;
    overflow-y: auto;
    overflow-x: hidden;
}
.button{
    height: 40px;
    line-height: 40px;
    text-align: center;
    font-size: 1.4rem;
    color: darkorchid;
    border-top: 1px solid beige;
}
</style>