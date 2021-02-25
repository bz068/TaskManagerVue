<template>
  <form @submit="onsubmit">
    <div class="mb-3">
      <label for="title" class="form-label">Title</label>
      <input
        type="text"
        v-model="title"
        class="form-control"
        id="title"
        autocomplete="off"
      />
    </div>
    <div class="mb-3">
      <label for="date" class="form-label">Date</label>
      <input type="Date" v-model="date" class="form-control" id="date" />
    </div>
    <div class="mb-3 form-check">
      <input
        type="checkbox"
        v-model="reminder"
        class="form-check-input"
        id="check1"
      />
      <label class="form-check-label" for="check1">Remind Me</label>
    </div>
    <ErrorMsg msg="Please Enter All Fields" v-if="this.error" />
    <button type="submit" class="btn btn-primary">Add Task</button>
  </form>
</template>

<script>
import ErrorMsg from "./Error.vue";
export default {
  components: { ErrorMsg },
  name: "AddTask",
  data() {
    return {
      title: "",
      date: "",
      reminder: false,
      error: false,
    };
  },
  methods: {
    onsubmit(e) {
      e.preventDefault();

      if (!this.title || !this.date) {
        this.error = true;
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        title: this.title,
        date: this.date,
        reminder: this.reminder,
      };

      this.$emit("add-task", newTask);

      this.title = "";
      this.date = "";
      this.reminder = false;
      this.error = false;
    },
  },
};
</script>
