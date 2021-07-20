<template>
  <div class="contact">
    <h3>
      {{ contact.name }}
      <span class="icons">
        <i
          @click="$emit('delete-contact', contact.id)"
          class="fas fa-user-minus"
        ></i>
        <i
          @click="$emit('edit-contact', contact.id)"
          class="fas fa-user-edit"
        ></i
      ></span>
    </h3>
    <p>{{ contact.phoneNumber }}</p>
    <p>{{ contact.email }}</p>
  </div>
</template>
<script>
export default {
  name: "Contact",
  props: {
    contact: Object,
  },
  methods: {},
};
</script>
<style scope>
.fas {
  color: red;
  cursor: pointer;
  padding: 15px;
}
.fa-user-edit {
  color: steelblue;
}
.contact {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
}

.contact h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
