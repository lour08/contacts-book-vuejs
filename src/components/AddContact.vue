<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Contact</label>
      <input type="text" v-model="name" name="text" placeholder="Full Name" />
    </div>
    <div class="form-control">
      <label>Email</label>
      <input type="text" v-model="email" name="email" placeholder="Email" />
    </div>
    <div class="form-control">
      <label>Phone Number</label>
      <input
        type="number"
        v-model="phoneNumber"
        name="phoneNumber"
        placeholder="Phone Number"
      />
    </div>

    <input type="submit" value="Save Contact" class="btn btn-block" />
  </form>
</template>
<script>
export default {
  name: "AddContact",
  data() {
    return {
      name: "",
      email: "",
      phoneNumber: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.name) {
        alert("Please add a Contact");
        return;
      }
      const newContact = {
        id: Math.floor(Math.random() * 1000),
        name: this.name,
        email: this.email,
        phoneNumber: this.phoneNumber,
      };
      this.$emit("add-contact", newContact);

      console.log(newContact);

      (this.name = ""), (this.email = ""), (this.phoneNumber = "");
    },
  },
  props: {
    contact: Object,
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
</style>
