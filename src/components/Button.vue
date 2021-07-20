<template>
  <button :style="{ background: color }" class="btn" @click="onClick()">
    {{ message }} <i :class="icon"></i>
  </button>
</template>
<script>
export default {
  name: "Button",
  props: {
    message: String,
    color: String,
    icon: String,
  },
  methods: {
    onClick() {
      this.$emit("toggle-add-contact");
    },
  },
};
</script>
<style scoped>
.fa-minus-circle {
  color: white;
  padding: 3px;
}
.fa-user-plus {
  color: white;
  padding: 3px;
}
button {
  font-weight: bold;
}
</style>
