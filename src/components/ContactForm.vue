<template>
  <div>
      <h3>New Contact</h3>
      <v-form>
            <v-text-field 
                outlined 
                label="First Name" 
                v-model="form.firstName">
            </v-text-field>
            
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
            options: ["Home", "Office", "Cell"]
        };
    }

};
</script>

<style>

</style>