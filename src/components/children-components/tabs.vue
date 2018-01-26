<!-- 这里是编写content部分按钮的组件 -->
<template>
  <div class="tabs">
    <!-- 剩余的todo项 -->
    <div class="remainTodos">
      <span>{{ unFinishedTodo }} todo left</span>
    </div>

    <!-- todo的状态 -->
    <div class="state"
         v-for="state in states"
         :key="state"
         :class="[state , fillter === state ? 'actived' : '']"
         @click="toggleFillter(state)">
      <span>{{ state }}</span>
    </div>

    <!-- 清除所有的todo -->
    <div class="clearCompleted">
      <span @click="clearCompleted">
        Clear Completed
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props:{
      fillter : {
        type : String,
        required : true
      },
      todos : {
        type : Array,
        required : true
      }
  },
  data () {
    return {
      states : ['all','active','completed']
    };
  },

  //计算属性就是每一次数据变化是就回去调用这个方法来更新数据和页面
  computed: {
    //未完成todo事项
    unFinishedTodo(){
      return this.todos.filter(
        todo=>!todo.completed
      ).length;
    }
  },

  //mounted: {},

  methods: {
    clearCompleted(){

    },

    //按钮切换的方法
    toggleFillter(state){
      this.$emit('toggle',state);
    }
  }
}

</script>
<style scoped>
div{
  float: left;
}
.tabs{
  width: 600px;
  background-color: #ddd;
  position: relative;
}

/* 左边的样式 */
.remainTodos,.clearCompleted{
  font-size: 16px;
  height: 40px;
  color: rgb(87, 83, 83);
  display: table;
}

.remainTodos{
  float: left;
  margin-right: 130px;
}

.state{
  display: block;
  font-size: 16px;
  color: rgb(87, 83, 83);
  margin: 11px 5px 11px 0;
  cursor: pointer;
}

.clearCompleted{
  float: right;
}

.remainTodos span {
  display: table-cell;
  vertical-align: middle;
}

/* 中间的样式 */
.state span{
  display: table-cell;
  vertical-align: middle;
}

/* 右边的样式 */
.clearCompleted span{
  display: table-cell;
  vertical-align: middle;
}

/* 按钮被选中时样式 */
.actived{
  border-color: red;
  border: 1px solid;
  border-radius: 10px;
  padding: 0 6px;
}

.actived span{

}


</style>
