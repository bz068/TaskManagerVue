<template>
  <div class="d-flex justify-content-between">
    <h2>{{ msg }}</h2>
    <Button
      @btn-click="$emit('toggleComp')"
      :title="addtask ? 'Close' : 'Add Task'"
      :color="addtask ? 'red' : 'green'"
    />
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  components: { Button },
  name: "Header",
  props: {
    msg: String,
    addtask: Boolean,
  },
};
</script>
