<template>
  <v-responsive class="align-center text-center fill-height px-13 pb-10 h-auto bg-tertiary">

    <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 mb-16 text-primary">books</h1>

    <v-card class="mx-auto pa-0 mb-5 bg-transparent" width="1000px" style="box-shadow: none;">
      <v-row>
        <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
          <router-link class="text-decoration-none" :to="card.route">
            <v-hover v-slot:default="{ isHovering, props }">
              <v-card v-bind="props">
                <v-parallax :src="card.src" class="align-center"
                  :gradient="isHovering ? 'to bottom, rgba(0,0,0,.4), rgba(0,0,0,.9)' : 'to bottom, rgba(0,0,0,.2), rgba(0,0,0,.7)'"
                  height="300px" cover>
                  <v-card-title :class="isHovering ? 'text-secondary' : 'text-quarternary'"
                    class="text-uppercase text-h3 font-weight-bold" v-text="card.title"></v-card-title>
                </v-parallax>
              </v-card>
            </v-hover>
          </router-link>
        </v-col>
      </v-row>
    </v-card>
  </v-responsive>
</template>

<script setup>
import { ref } from "vue";

const cards = ref([
  {
    title: 'Self-Improvement',
    src: 'https://img.freepik.com/free-photo/improvement-potential-excellence-diagram-graphic-concept_53876-133936.jpg?w=996&t=st=1693108453~exp=1693109053~hmac=54add6e0612909d9d7627cd8ae073141509115552ae561268d26fce888785851',
    flex: 12,
    route: '/self-improvement'
  },
  {
    title: 'Novel',
    src: 'https://img.freepik.com/free-photo/open-book-with-fairytale-scene_52683-107844.jpg?w=1060&t=st=1693108547~exp=1693109147~hmac=aeddf642c7e2efa02f3dd3b65f90f1540252f6c6bbf470db313b85cc018c3a32',
    flex: 6,
    route: '/novel'
  },
  {
    title: 'biography',
    src: 'https://img.freepik.com/free-photo/abstract-truth-concept-composition_23-2149051356.jpg?w=1060&t=st=1693108610~exp=1693109210~hmac=669e8a48a53090e88fabb64f36b3610261b3148beb272b3d8d48a37bc958be59',
    flex: 6,
    route: '/biography'
  }


])
</script>
