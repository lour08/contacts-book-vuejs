<template>
  <div :key="contact.id" v-for="contact in contacts">
    <Contact
      @toggle-reminder="$emit('toggle-reminder', contact.id)"
      :contact="contact"
      @delete-contact="$emit('delete-contact', contact.id)"
      @edit-contact="$emit('edit-contact', contact.id)"
    >
    </Contact>
  </div>
</template>
<script>
import Contact from "./Contact";
export default {
  name: "Contacts",
  components: {
    Contact,
  },
  emits: ["delete-contact", "edit-contact"],
  props: {
    contacts: Array,
  },
};
</script>
