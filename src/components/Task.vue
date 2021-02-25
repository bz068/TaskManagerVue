<template>
  <div
    @dblclick="$emit('set-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'card text-center mt-2']"
    style="width: 99%;"
  >
    <div class="card-body">
      <h5 class="card-title">
        {{ task.title }}
        <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
      </h5>
      <p class="card-text">
        {{ moment(String(task.date)).format("MM/DD/YYYY") }}
      </p>
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "Task",
  props: {
    task: Object,
  },

  data() {
    return {
      moment: moment,
    };
  },
};
</script>

<style scoped>
.reminder {
  border-left: 5px solid green;
}
.card-body h5 {
  display: flex;
  justify-content: space-between;
  padding: 0 10px;
}
.fas {
  color: red;
  cursor: pointer;
}
</style>

<style scoped>
.card {
  animation: fadein 1s;
}
</style>
