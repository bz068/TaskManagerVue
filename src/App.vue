<template>
  <div class="main">
    <div class="container mt-4">
      <Header
        :addtask="addTaskComponent"
        @toggleComp="toggleComp"
        msg="Task Manager"
      />
      <AddTask v-if="addTaskComponent" @add-task="addTask" />
      <p class="font-weight-light mt-3">
        Double Click On Task To Set Reminder Off
      </p>
      <Tasks
        @set-reminder="setReminder"
        @delete-task="deleteTask"
        :tasks="tasks"
      />
    </div>
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
    AddTask,
    Tasks,
  },
  data() {
    return {
      tasks: [],
      addTaskComponent: false,
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    setReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    toggleComp() {
      this.addTaskComponent = !this.addTaskComponent;
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        title: "Doctors Appointment",
        date: "2/25/2021",
        reminder: true,
      },
      {
        id: 2,
        title: "Car Service",
        date: "02/27/2021",
        reminder: true,
      },
      {
        id: 3,
        title: "Vet Appointment",
        date: "02/28/2021",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.main {
  width: 100%;
  max-width: 650px;
  margin: 30px auto;
  border: 1px solid;
  padding: 10px;
}
</style>
