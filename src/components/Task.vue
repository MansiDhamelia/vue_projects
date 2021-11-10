<template>
  <div @dblclick="$emit('toggle', task.id)" :class="[task, reminder ? 'reminder' : '', 'task']">

    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fa fa-close"> </i>
    </h3>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
};
</script>

<style scoped>
.fa {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  text-align: left;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>