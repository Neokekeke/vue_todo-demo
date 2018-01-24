<!-- 这里是编写通用的footer组件 -->
<template>
  <div id="footer">

    <span>
      Neo needs to be better
    </span>

  </div>
</template>

<script>
export default {
  data () {
    return {
    };
  },

  components: {},

  computed: {},

  // 生命周期钩子，页面初始化时执行的操作
  mounted: {},

  methods: {}
}

</script>


<style scoped>

#footer{
  text-align: center;
  font-family: -apple-system,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Microsoft YaHei,Source Han Sans SC,Noto Sans CJK SC,WenQuanYi Micro Hei,sans-serif;
  position: fixed;
  left: 50%;
  top: 80%;
  transform: translate(-50%,-50%);
  font-size: 30px;
  font-weight: 200;
}


</style>
