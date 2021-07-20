<template>
  <header>
    <h2>{{ title }}</h2>
    <Button
      @toggle-add-contact="$emit('toggle-add-contact')"
      :message="showAddContact ? 'Close' : 'Add Contact'"
      :color="showAddContact ? 'darkred' : 'green'"
      :icon="showAddContact ? 'fas fa-minus-circle' : 'fas fa-user-plus'"
    ></Button>
  </header>
</template>
<script>
import Button from "./Button";

export default {
  name: "Header",
  props: {
    title: String,
    showAddContact: Boolean,
  },
  components: {
    Button,
  },
};
</script>
<style scoped>
h2 {
  font-weight: bold;
  font-size: 32px;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
