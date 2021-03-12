<template>
  <div>
      <h3 class="deep-purple--text">New Contact</h3>
      <v-form @submit.prevent="handleSubmit" ref="contactForm">
            <v-text-field 
                outlined 
                label="First Name" 
                v-model="form.firstName"
                :rules="validators.firstName">
            </v-text-field>

            <v-text-field 
                outlined 
                label="Last Name" 
                v-model="form.lastName"
                :rules="validators.lastName">
            </v-text-field>

             <v-text-field 
                outlined 
                label="Phone" 
                v-model="form.phone"
                :rules="validators.phone">>
            </v-text-field>

            <v-select 
                outlined
                :items="options" 
                label="Phone Type" 
                v-model="form.type">
            </v-select>

            <v-text-field 
                outlined 
                label="Email" 
                v-model="form.email"
                :rules="validators.email">>
            </v-text-field>

            <v-btn type="submit" color="deep-purple" dark>Submit</v-btn>

      </v-form>
  </div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                firstName: "",
                lastName: "",
                phone: "",
                type: "",
                email: ""
            },
            options: ["Home", "Office", "Cell"],

            validators: {
                firstName: [
                    val => !!val || "Contact first name is required",
                    val => val.length < 25 || "First name must be less than 25 characters"
                ],
                lastName: [
                    val => val.length < 25 || "Last name must be less than 25 characters"
                ],
                phone: [
                    val => !!val || "Phone number is required",
                    val => val.length === 10 || "Phone number must be 10 characters"
                ],
                email: [
                    val => val.includes("@") || "Enter a valid email address"
                ],             
            }
        };
    },
    method: {
        handleSubmit() {
            const isValid = this.$refs.contactForm.validate();
            if (!isValid) {
                // Form is not valid. Exit the method
                return;
            }

            this.$emit('contact-submit', this.form);
            // emits event to parent (phonebook)
            // then clears the form
            this.form = {
                firstName: "",
                lastName: "",
                phone: "",
                type: "",
                email: ""
            };
            this.$refs.contactForm.resetValidation();
        }
    }
};
</script>

<style>

</style>