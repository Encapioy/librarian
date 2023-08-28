<template>
  <v-responsive class="align-center text-center fill-height px-13 pb-13 h-auto">

    <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 mb-16 text-primary">benefit of reading</h1>



    <v-row>
      <v-col v-for="benefit in benefits" :key="benefit.title" :cols="benefit.flex">
        <v-hover v-slot:default="{ isHovering, props }">
          <v-card v-bind="props" :color="isHovering ? 'secondary' : 'tertiary'" class="mx-auto h-100 py-5 text-primary"
            width="370">
            <v-icon class="text-h3" aria-hidden="false" :icon="benefit.icon"></v-icon>

            <v-card-text class="text-h6 font-weight-bold text-uppercase" v-text="benefit.title"></v-card-text>

            <v-card-text class="text-body-2" v-text="benefit.text"></v-card-text>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </v-responsive>
</template>

<script setup>
import { ref } from "vue";

const benefits = ref([
  {
    icon: 'mdi-brain',
    title: 'Improve Intelligence',
    text: 'Reading can help keep the brain in order to always carry out its functions perfectly. When reading, the brain is required to think, analyze various problems, find solutions and solutions to find new things.',
    flex: 4
  },
  {
    icon: 'mdi-finance',
    title: 'Good Concentration Level',
    text: 'have the ability to make decisions quickly and accurately. Reading books makes our brains focus and concentrate. This helps us in developing objectivity skills.',
    flex: 4
  },
  {
    icon: 'mdi-pencil',
    title: 'Growing Writing Ability',
    text: 'If your job requires you to write a lot, such as a journalist, public relations, or even a musician, reading books is highly recommended. A well-written book can be an inspiration for you in composing beautiful and interesting words.',
    flex: 4
  },
  {
    icon: 'mdi-face-man-shimmer',
    title: 'Provide Calmness',
    text: ' It is very possible if the body becomes relaxed while reading a book. Research has proven that reading spiritual books can lower blood pressure and calm the heart.',
    flex: 6
  },
  {
    icon: 'mdi-briefcase',
    title: 'Improve Discipline',
    text: 'Finding time to read is something that needs to be done. But which of us has made a schedule to read a book every day? Maybe just a little bit. For this reason, adding book reading activities to our daily schedule and sticking to that schedule will improve discipline.',
    flex: 6
  },
])
</script>
