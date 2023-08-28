<template>
  <v-app-bar scroll-behavior="hide" class="bg-tertiary">
    <v-app-bar-title class="text-h4 font-weight-bold text-primary">

      Librarian.
    </v-app-bar-title>
    <v-spacer></v-spacer>

    <div class="pe-16">

      <v-btn class="me-5">
        <router-link class="text-decoration-none text-primary font-weight-bold" to="/">Home</router-link>
      </v-btn>

      <v-btn class="me-5">
        <router-link class="text-decoration-none text-secondary font-weight-bold" to="/self-improvement">Self-Improvement</router-link>
      </v-btn>

      <v-btn class="me-5">
        <router-link class="text-decoration-none text-secondary font-weight-bold" to="/novel">Novel</router-link>
      </v-btn>

      <v-btn class="me-5">
        <router-link class="text-decoration-none text-secondary font-weight-bold" to="/biography">Biography</router-link>
      </v-btn>

    </div>
  </v-app-bar>
</template>

<script setup>
  //
</script>

