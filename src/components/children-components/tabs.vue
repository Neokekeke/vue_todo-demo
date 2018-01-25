<!-- 这里是编写content部分按钮的组件 -->
<template>
  <div class="tabs">
    <!-- 剩余的todo项 -->
    <div class="remainTodos">
      <span v-model="remainTodos">{{ remainTodos }}</span>
    </div>

    <!-- todo的状态 -->
    <div class="state"
         v-for="state in states"
         :key="state"
         :class="[state , fillter === state ? 'actived' : '']"
         @click="toggleFillter(fillter)">
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
        require : true
      }
  },
  data () {
    return {
      remainTodos : 'one todo left',
      states : ['all','active','completed']
    };
  },

  computed: {},

  mounted: {},

  methods: {
    clearCompleted(){

    },
    toggleFillter(){

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
  box-sizing: border-box;
  padding: 6px 6px;
}

.actived span{

}


</style>
