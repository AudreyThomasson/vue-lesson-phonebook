<template>
  <v-app>
    <v-app-bar app color="deep-purple" dark>
      <div class="d-flex align-center">
        

        <h3>My Vue-tiful Phonebook</h3>
      </div>

      <v-spacer></v-spacer>

      
    </v-app-bar>

    <v-main class="ma-5">
      <phonebook />
    </v-main>
  </v-app>
</template>

<script>
import Phonebook from "./components/Phonebook";

export default {
  name: "App",
  components: { Phonebook }
};
</script>
