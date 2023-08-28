<template>
  <v-responsive class="align-center text-center fill-height h-auto">

    <v-footer class="d-flex flex-column mt-n2 mb-n2 mx-n5">
      <div class="bg-secondary d-flex w-100 align-center justify-center px-4 py-5">

        <v-btn color="quarternary" v-for="icon in icons" :key="icon" class="mx-4" :icon="icon" variant="plain"
          size="small"></v-btn>
      </div>

      <div class="px-4 py-2 bg-primary text-center text-tertiary w-100">
        &copy; Muhammad Fidiansyah {{ new Date().getFullYear() }} All Right Reserved
      </div>
    </v-footer>

  </v-responsive>
</template>

<script setup>
import { ref } from "vue";

const icons = ref([
  'mdi-facebook',
  'mdi-twitter',
  'mdi-linkedin',
  'mdi-instagram',
])
</script>