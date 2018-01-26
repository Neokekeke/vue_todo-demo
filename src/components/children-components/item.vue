<!-- 这里是编写content部分TODO的内容子组件，显示TODOlist -->
<template>

  <div :class="['todo-item',todo.completed ? 'completed' : '']">

    <div class="left">
        <input
          type="checkbox"
          v-model="todo.completed"
          class="toggle">
    </div>

   <div class="content">
    <label>
      {{ todo.content }}
    </label>
   </div>

   <div class="delete">
    <button @click="deleteTodo">
    </button>
   </div>

  </div>

</template>

<script>
export default {
  props: {
      todo : {
        type : Object,
        require : true
      }
  },
  data () {
    return {

    };
  },

  //mounted: {},

  methods: {
    deleteTodo(){
      this.$emit('delete',this.todo.id);
    }
  }
}

</script>
<style scoped>
/* todo整一条栏的样式 */
.todo-item{
  position: relative;
  border-bottom: 1px solid rgba(0,0,0,0.10);
  background-color: #ddd;
  width: 600px;
  height: 60px;
  float: left;
}

/* 左边div */
.left{
  position: absolute;
  left: 25px;
  top: 50%;
  transform: translate(-50%,-50%);
  width: 40px;
  height: 40px;
}

/* 中间todo内容的样式 */
.content{
  transition: color 0.5s;
  color: #999;
  font-size: 30px;
  width: 500px;
  position: absolute;
  left: 50%;
  height: 35px;
  top: 50%;
  transform: translate(-50%,-50%);
  display: table;
  margin-left: 10px;
}

input{
  border: none;
}

label{
  border: none;
  border-width: 0;
  display: table-cell;
  vertical-align: middle;
}

.completed{
  width: 100%;
}

.completed label{
  color: rgb(125,125,125);
  text-decoration: line-through;
}

/* CheckBox的样式 */
.toggle{
  width: 100%;
  height: 100%;
  margin: 0 auto;
  border: none;
  appearance: none;
  opacity: 0.6;
}

.toggle:hover{
  opacity: 1;
}

.toggle::after{
  content: url("../../assets/done.png");
}

.toggle:checked::after{
  content: url("../../assets/done1.png");
}

/* 删除按钮样式 */
.delete{
  position: absolute;
  top: 50%;
  right: -20px;
  transform: translate(-50%,-50%);
  width: 40px;
  height: 40px;

}

.delete button{
  cursor: pointer;
  width: 100%;
  height: 100%;
  transition: color 0.5s ease-out;
  outline: none;
  color: #cc9a9a;
  border: none;
  font-size: 25px;
}

.todo-item:hover .delete button::after{
  content: 'x';
  border: none;
}


</style>
