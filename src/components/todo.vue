<!-- 这里编写的是TODO的content内容部分的组件是container -->
<template>
  <section id="todo">

    <!-- todo的顶部input输入框 -->
    <input
      class="add-input"
      type="text"
      autofocus="autofocus"
      placeholder="接下来做些什么呢？"
      @keyup.enter="addToDo">

    <!-- todo的中间content部分 -->
    <Item :todo="todo"></Item>

    <!-- todo的底部按钮部分 -->
    <Tabs :fillter="fillter"></Tabs>

  </section>
</template>

<script>
import Item from '../components/children-components/item.vue'
import Tabs from '../components/children-components/tabs.vue'

export default {
  components:{
    Item,
    Tabs
  },
  data () {
    return {
        todo : {
            id : 0,
            content : 'this is todo',
            completed : false
        },
        fillter : 'all'
    };
  },

  computed: {},

  mounted: {},

  methods: {
    addToDo(){

    }
  }
}

</script>
<style scoped>
  #todo{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    width: 600px;
    background-color: #999;
    opacity: 0.6;
  }

  #todo:hover{
    opacity: 1;
    background-color: #fff;
  }

  .add-input{
    width: 100%;
    height: 60px;
    font-size: 40px;
    padding: 5px 0 5px 0;
    display: block;
    border: 0;
    text-indent: 30px;
    word-break: break-all;
    word-wrap: break-word;
    white-space: pre-wrap;
  }


</style>
