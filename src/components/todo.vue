<!-- 这里编写的是TODO的content内容部分的组件是container -->
<template>
  <section id="todo">

    <!-- todo的顶部input输入框 -->
    <input
      class="add-input"
      type="text"
      autofocus="autofocus"
      placeholder="接下来做些什么呢？"
      @keyup.enter="addToDo"
    >
    <Item></Item>
    <Tabs></Tabs>

  </section>
</template>

<script>
import Item from '../components/item.vue'
import Tabs from '../components/tabs.vue'

export default {
  components:{
    Item,
    Tabs
  },
  data () {
    return {
    };
  },

  components: {},

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

  .add-input{
    width: 100%;
    height: 30px;
    margin:0 0 0 0;
    font-size: 30px;
    padding: 5px 0 5px 0;
  }

  .add-input:hover{
    opacity: 1;
    background-color: #fff;
  }


</style>
