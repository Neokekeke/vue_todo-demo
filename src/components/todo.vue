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
      :disabled="disableInput"
    >

    <!-- todo的中间content部分 -->
    <Item
        :todo="todo"
        v-for="todo in fillterTodos"
        :key="todo.id"
        @delete="deleteTodo"
    />

    <!-- 超出5条todo的提醒 -->
    <Toast v-show="checkTodoLen"
    />

    <!-- todo的底部按钮部分 -->
    <Tabs :fillter="fillter"
          :todos="todos"
          @toggle="toggleBtn"
          @clearAllCompleted="clearAllCompleted"
    />

  </section>
</template>

<script>
import Item from '../components/children-components/item.vue'
import Tabs from '../components/children-components/tabs.vue'
import Toast from '../components/children-components/toast.vue'

let id = 0;
export default {
  components:{
    Item,
    Tabs,
    Toast
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
      else{
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

    // 检查todo的长度是否大于5
    checkTodoLen(){
        const todoLength = this.todos.length>=5;
        if(todoLength == true){
          return todoLength;
        }
        return todoLength;
    },

    // 禁用大于输入5条todo的输入框
    disableInput(){
       if(this.todos.length >= 5){
         return true;
       }
       return false;
    }

  },

  // watch监听列表属性
  // watch : {},

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
        (todo) => { //这个todo是需要绑定给子组件的todo子项
          console.log("kk",todo.id);
          if(todo.id === id){
              return todo.id
          }
      }),1)
    },

    //切换按钮方法
    toggleBtn(state){
      this.fillter = state; //从子组件中获取的数据，再改变子组件的数据
    }
  },

  //清除所有已经完成的todos
  clearAllCompleted(){
    this.todos = this.todos.filter(todo=>!todo.completed);
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
    text-indent: 60px;
    word-break: break-all;
    word-wrap: break-word;
    white-space: pre-wrap;
  }


</style>
