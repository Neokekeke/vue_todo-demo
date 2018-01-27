<!-- 这里是弹窗的组件 -->
<template>
  <div id="toast1">
    <span>请先完成当前的5条Todos哦~</span>
  </div>
</template>

<script>
export default {
  props : {

  },
  data () {
    return {
    };
  },

  components: {},

  computed: {},

  // mounted: {},

  methods: {}
}

</script>
<style scoped>

#toast1{
  color: rgb(243, 236, 236);
  text-align: center;
  height: 50px;
  clear: both;
  background-color: rgb(250, 141, 102);
}

#toast1 span{
  line-height: 50px;
  font-size: 20px;
}

</style>
