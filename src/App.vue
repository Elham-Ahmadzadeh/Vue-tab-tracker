<template>
  <div class="container">
    <Header
      @toggle-add-task="toggleAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>

    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "hjhbjhv jhjhvhv",
        day: "nmnnbjh tgcgd",
        reminder: true,
      },
      {
        id: 2,
        text: "hjhbjhv jhjhvhv",
        day: "nmnnbjh tgcgd",
        reminder: true,
      },
      {
        id: 3,
        text: "hjhbjhv jhjhvhv",
        day: "nmnnbjh tgcgd",
        reminder: false,
      },
    ];
  },
  data() {
    return {
      tasks: [],
      showAddTask: true,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("are you sure ?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
</style>
