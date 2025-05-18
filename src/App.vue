<script setup>

</script>

<template>
  <div class="main">

    <!-- 标题 -->
    <h1>ToDo App</h1>

    <!-- 输入框 -->
    <div class="inputBox">
      <input type="text" placeholder="Add a new task" />
      <button>Add</button>

    </div>

    <!-- 任务列表 -->
    <div class="taskBox">
      <div class="taskItem" v-for="_ in 10">
        <input type="checkbox" />
        <span>Task 1</span>
        <button>Delete</button>
      </div>
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
</style>
