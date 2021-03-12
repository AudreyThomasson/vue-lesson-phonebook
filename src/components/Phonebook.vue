// parent of contact form
<template>
    <div>
        <v-row>
            <v-col :md="8" :sm="12">
                <contacts-table :contacts="contacts" />
            </v-col>
            <v-col :md="4" :sm="12">
                <contact-form @contact-submit="addContact"/>
                <!-- listen for an event on the form, then addContact -->
            </v-col>    
        </v-row>
    </div>
</template>

<script>
import ContactForm from './ContactForm';
import ContactsTable from "./ContactsTable"

export default {
    components: { ContactForm, ContactsTable },

    data() {
        return {
            contacts:[]
        };
    },
    mounted() {
        const existingContacts = JSON.parse(localStorage.getItem("contacts"));
        this.contacts = existingContacts || [];
    },
    methods:{
        addContact(newContact) {
            this.contacts.push(newContact);
            // when you hear a submit on the form, push it into contacts array
            // and save in localStorage
            localStorage.setItem("contacts", JSON.stringify(this.contacts));
        }
    }
};
</script>

<style>

</style>