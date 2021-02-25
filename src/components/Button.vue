<template>
  <button :style="{ background: color }" @click="onClick" class="btn-sm btn">
    {{ title }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    title: String,
    color: {
      type: String,
      default: "green",
    },
  },
  methods: {
    onClick() {
      this.$emit("btn-click");
    },
  },
};
</script>

<style scoped>
button {
  color: white;
}
</style>
