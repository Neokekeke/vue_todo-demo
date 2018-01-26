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
    <Item
        :todo="todo"
        v-for="todo in fillterTodos"
        :key="todo.id"
        @delete="deleteTodo"
    />

    <!-- todo的底部按钮部分 -->
    <Tabs :fillter="fillter"
          :todos="todos"
          @toggle="toggleBtn"
    />

  </section>
</template>

<script>
import Item from '../components/children-components/item.vue'
import Tabs from '../components/children-components/tabs.vue'

let id = 0;
export default {
  components:{
    Item,
    Tabs
  },
  data () {
    return {
        todos :[],
        fillter : 'all',
    };
  },

  computed: {
    fillterTodos(){
      if(this.fillter == 'all'){
        return this.todos;
      }
      const completed = this.fillter === 'completed';
      return this.todos.filter(todo=>completed === todo.completed);
      // if(completed){
      //   return this.todos.filter(todo=>todo.completed);
      // }
      // else{
      //   return this.todos.filter(todo=>!todo.completed);
      // }
    }

  },

  //mounted: {},

  methods: {
    addToDo(e){
      this.todos.unshift({ //在数组的前面添加一项
        id : id++,
        content : e.target.value.trim(), //去除前后空格
        completed : false
      });
      e.target.value = '';
      console.log(e,this.id,id);
    },

    deleteTodo(id){
      //清除选中的一项
      this.todos.splice(this.todos.findIndex(
        (id)=>{
          if(this.todos.id === id){
            return id;
          }}),1)
    },

    //切换按钮方法
    toggleBtn(state){
      this.fillter = state; //从子组件中获取的数据，再改变子组件的数据
    }
  }
}

</script>
<style scoped>
  #todo{
    position: fixed;
    top: 40%;
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
    text-indent: 60px;
    word-break: break-all;
    word-wrap: break-word;
    white-space: pre-wrap;
  }


</style>
