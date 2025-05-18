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
  taskList.value.splice(index, 1)
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
    <h1>ToDo App</h1>

    <!-- 输入框 -->
    <div class="inputBox">
      <input v-model="newTask" type="text" placeholder="Add a new task" />
      <button @click="Add">Add</button>

    </div>

    <!-- 任务列表 -->
    <div class="taskBox normal" v-for="(item, index) in taskList" key="item.id">

      <div class="left" :class=" item.completed && 'completed' ">
        <input v-model="item.completed" type="checkbox" />
        <span>{{ item.name }}</span>
      </div>

      <button @click="Del(index)">Delete</button>
    </div>

  </div>
</template>

<style scoped>
.main {
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: center;
  height: 100vh;

}

.inputBox {
  padding: 60px 0;
}


.taskBox {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 400px;
}

.normal {
  font-size: 20px;
  padding: 10px 0;
}
.completed > span {
  text-decoration: line-through;
  opacity: 0.4;
}
</style>
