<template>
  <div class="container">
    <Header title="Task Tracker"></Header>
    <AddTask @add-task="addTask" />
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",

  components: {
    Header,
    Tasks,
    AddTask,
  },
  data: function () {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      // console.log("task", id);
      if (confirm("Arey you sure?")) {
        // 过滤掉 task.id 为 id 的 task
        this.tasks = this.tasks.filter((task) => {
          return task.id !== id;
        });
      }
    },
    toggleReminder(id) {
      console.log(id);
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: "DJAINGO REST API",
        day: "Tomorrow",
        reminder: true,
      },
      {
        id: 2,
        text: "DJAINGO",
        day: "Tomorrow",
        reminder: true,
      },
      {
        id: 3,
        text: "VUEJS",
        day: "Tomorrow",
        reminder: true,
      },
      {
        id: 4,
        text: "JAVASCRIPT",
        day: "Tomorrow",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.body {
  font-family: sans-serif;
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
.btn {
  display: inline-block;
  background: black;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
