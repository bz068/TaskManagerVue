<template>
  <div class="alert alert-danger" role="alert">{{ msg }}</div>
</template>

<script>
export default {
  name: "ErrorMsg",
  props: {
    msg: String,
  },
};
</script>

<style scoped>
.alert {
  animation: fadein 0.5s linear;
}
</style>
