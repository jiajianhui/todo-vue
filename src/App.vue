<script setup>
import { ref } from 'vue';

const newTask = ref('')


// 添加函数
function Add() {

  // 判断
  if (newTask.value.trim() === "") {
    return alert("Please enter the task")
  }

  // 添加任务
  taskList.value.push({
    id: taskList.value.length + 1, 
    name: newTask.value, 
    completed: false
  })


  // 清空输入框
  newTask.value = ""
}

// 删除函数
function Del(index) {
  const confirmed = confirm("Are you sure you want to delete it?")
  if (confirmed) {
    taskList.value.splice(index, 1)
  }
  
}

// 任务列表
const taskList = ref([
  { id: 1, name: 'Task 1', completed: false },
  { id: 2, name: 'Task 2', completed: false },
  { id: 3, name: 'Task 3', completed: false },
])

</script>

<template>
  <div class="main">

    <!-- 标题 -->
    <div class="title">ToDo App</div>

    <!-- 输入框 -->
    <div class="inputBox">
      <input v-model="newTask" type="text" placeholder="Add a new task" />
      <div class="btnBox">
        <button @click="Add">Add</button>
      </div>

    </div>

    <!-- 任务列表 -->
    <div class="taskBox" v-for="(item, index) in taskList" key="item.id">

      <div class="left" :class=" item.completed && 'completed' ">
        <input v-model="item.completed" type="checkbox" />
        <span>{{ item.name }}</span>
      </div>

      <button @click="Del(index)">Delete</button>
    </div>

  </div>
</template>

<style scoped>
* {
  box-sizing: border-box;
}
.title {
  font-size: 40px;
  font-weight: bold;
  margin-top: 60px;
}
.main {
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: center;
  height: 100vh;

}

.inputBox {
  margin: 40px 0 30px 0;
  position: relative;
}
.inputBox > input {
  /* 移除边框默认样式 */
  outline: none;

  padding: 14px 20px;
  border: 1.5px solid #dedede;
  border-radius: 14px;
  font-size: 20px;
  line-height: 20px;
  width: 400px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0);
  transition: all ease-in-out .3s;
}
.inputBox>input:focus {
  border-color: #161616;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}
.inputBox>input::placeholder {
  color: #b5b5b5;
  font-weight: 100;
}

.inputBox > .btnBox {
  position: absolute;
  top: 0;
  right: 0;
  height: 100%;
  padding: 6px;
}
.inputBox> .btnBox button {
  border: none;
  font-size: 20px;
  line-height: 16px;
  padding: 0 24px;
  border-radius: 10px;
  height: 100%;
  background-color: #161616;
  color: white;

}


.taskBox {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 400px;
  font-size: 20px;
  padding: 14px 20px;
  border-radius: 14px;
  border: 1px solid #e9e9e9;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
  margin: 10px 0;
  background-color: white;
}
.taskBox > button {
  border: none;
  padding: 10px 14px;
  border-radius: 8px;
  background-color: rgba(255, 39, 89, 0.1);
  color: rgba(255, 39, 89);
}

.completed > span {
  text-decoration: line-through;
  opacity: 0.4;
}
</style>
