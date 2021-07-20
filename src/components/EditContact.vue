<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Contact</label>
      <input
        type="text"
        v-model="contact.name"
        name="text"
        placeholder="Full Name"
      />
    </div>
    <div class="form-control">
      <label>Email</label>
      <input
        type="text"
        v-model="contact.email"
        name="email"
        placeholder="Email"
      />
    </div>
    <div class="form-control">
      <label>Phone Number</label>
      <input
        type="number"
        v-model="contact.phoneNumber"
        name="phoneNumber"
        placeholder="Phone Number"
      />
    </div>

    <input type="submit" value="Edit Contact" class="btn btn-block" />
    <div class="cancel">
      <button class="btn btn-cancel" @click="onCancel()">
        Cancel <i class="fas fa-window-close"></i>
      </button>
    </div>
  </form>
</template>
<script>
export default {
  name: "EditContact",
  data() {
    return {
      contact: {},
    };
  },
  props: {
    openEditContacts: Boolean,
    contactToEdit: Object,
  },
  methods: {
    onsubmit(e) {
      e.preventDefault();
      if (!confirm("Are you sure that you want to edit this")) {
        this.$emit("edit-contact", this.contact);
      } else {
        return;
      }
    },
    onCancel() {
      this.$emit("cancel-edit-contact");
    },
  },
  created() {
    this.contact = this.contactToEdit;
  },
};
</script>
<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
.btn-cancel {
  background: red;
  font-weight: bold;
}
.fa-window-close {
  color: white;
  padding: 2px;
}
</style>
