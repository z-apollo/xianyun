<template>
  <div style="padding:100px;">
    <div class="btns">
      <span v-for="(item, index) in ['新闻', '娱乐', '体育']" 
      :key="index"
      @click="handleClick(index)"
      :class="{active: current === index}"
      >{{item}}</span>
    </div>

    <div v-if="current === 0">
      <p>11111111111111111111</p>
      <p>11111111111111111111</p>
      <p>11111111111111111111</p>
    </div>

    <div v-if="current === 1">
      <p>22222222222222222222</p>
      <p>22222222222222222222</p>
      <p>22222222222222222222</p>
    </div>

    <div v-if="current === 2">
      <p>33333333333333333333</p>
      <p>33333333333333333333</p>
      <p>33333333333333333333</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
        //一个框架的学习可以通过tab栏来总结，该例子最重要的核心就是当前的下标的变量
        current: 0
    };
  },
  methods:{
      handleClick(index){
          //点击时候改变current
          this.current = index
          console.log(this.current)
      }
  }
};
</script>

<style scoped lang="less">
.btns {
  margin-bottom: 20px;
  span {
    cursor: pointer;
    border: 1px #ddd solid;
    padding: 10px;
  }
  .active {
    color: red;
    border-color: red;
  }
}
</style>