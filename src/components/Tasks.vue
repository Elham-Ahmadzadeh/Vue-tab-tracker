<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
     @toggle-reminder="$emit('toggle-reminder', task.id)"
     @delete-task="$emit('delete-task', task.id)" :task="task" />
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  components: {
    Task,
  },
  emits: ["delete-tasks", 'toggle-reminder'],

  name: "Tasks",
  props: {
    tasks: Array,
  },
};
</script>
