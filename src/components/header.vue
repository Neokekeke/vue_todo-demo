<!-- 这里是编写通用的header组件 -->
<template>
  <div id="header">
    <span>
      Neo's TODO
    </span>
  </div>
</template>

<script>

import Item from '../components/children-components/item.vue'
export default {
  components:{
    Item
  },
  data () {
    return {
    };
  },

  computed: {},

  //mounted: {},

  methods: {}
}

</script>
<style scoped>

#header{
  position: fixed;
  top: 10%;
  left: 50%;
  transform: translate(-50%,-50%);
  font-size: 50px;
  font-family:-apple-system,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Microsoft YaHei,Source Han Sans SC,Noto Sans CJK SC,WenQuanYi Micro Hei,sans-serif;
  color: #fff;
  text-align: center;
  font-weight: 300;
}


</style>
