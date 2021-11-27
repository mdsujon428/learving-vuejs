<template>
  <div class="container">
    <Header 
    @toggle-add-task="toggleAddTask"
    title="Add Task" 
    :showAddTask="showAddTask"
    />
    <div v-if="showAddTask" @showTask-toggle="toggleShowTask">
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
import Header from "./components/Header/Header.vue";
import Tasks from "./components/Tasks/Tasks.vue";
import AddTask from "./components/Tasks/AddTask/AddTask.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
       
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 2:30px",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at School",
        day: "March 3rd 1:30px",
        reminder: true,
      },
      {
        id: 3,
        text: "Food Shopping",
        day: "March 4rd 11:00am",
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
body {
  font-family: "Poppins", sans-serif;
  background: #fff;
}
.container {
  max-width: 600px;
  min-height: 300px;
  margin: 30px auto;
  overflow: auto;
  border: 1px solid steelblue;
  background: #fff;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}

/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
