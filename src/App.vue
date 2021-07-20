<template>
  <div class="container">
    <Header
      @toggle-add-contact="toggleAddContact"
      title="Contact Book"
      :showAddContact="showAddContact"
    ></Header>
    <div v-if="showAddContact">
      <AddContact @add-contact="addContact" />
    </div>
    <Contacts
      @delete-contact="deleteContact"
      @edit-contact="editContact"
      :contacts="contacts"
    ></Contacts>
    <div v-if="openEditContacts">
      <EditContact
        :contactToEdit="contactToEdit"
        @edit-contact="editContact"
        :openEditContacts="openEditContacts"
        @cancel-edit-contact="cancelEdit"
      />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Contacts from "./components/Contacts.vue";
import AddContact from "./components/AddContact.vue";
import EditContact from "./components/EditContact.vue";
export default {
  name: "App",
  components: {
    Header,
    Contacts,
    AddContact,
    EditContact,
  },
  data() {
    return {
      contacts: [],
      showAddContact: false,
      openEditContacts: false,
      contactToEdit: Object,
    };
  },
  methods: {
    cancelEdit() {
      this.openEditContacts = false;
    },
    toggleAddContact() {
      this.showAddContact = !this.showAddContact;
    },

    addContact(contact) {
      this.contacts.push(contact);
      this.showAddContact = !this.showAddContact;
    },
    deleteContact(id) {
      if (confirm("This Contact will be deleted permanently. Are you sure?"))
        this.contacts = this.contacts.filter((contact) => contact.id !== id);
    },
    editContact(id) {
      this.openEditContacts = !this.openEditContacts;
      this.contacts.forEach((contact) => {
        if (contact.id === id) {
          this.contactToEdit = contact;
        }
      });
    },
  },
  created() {
    this.contacts = [
      {
        id: 1,
        name: "First Contact",
        email: "Contact@email.com ",
        phoneNumber: "297892173",
      },
      {
        id: 2,
        name: "second Contact",
        email: "Contact@email.com ",
        phoneNumber: "297892173",
      },
      {
        id: 3,
        name: " Third Contact",
        email: "Contact@email.com ",
        phoneNumber: "297892173",
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;1,300;1,400;1,600&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Open Sans", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
