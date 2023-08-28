<style>
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: .9;
  position: absolute;
  width: 100%;
}
</style>

<template>
  <v-responsive class="align-center fill-height px-13 pb-13 h-auto">

    <div class="h-screen">
      <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 text-primary">Biography</h1>
      <v-divider :thickness="3" class="mt-3 mb-16"></v-divider>

      <v-row class="mt-5">
        <v-col cols="4">
          <div class="rounded-shaped pa-1 bg-tertiary">
            <v-img
              src="https://img.freepik.com/free-photo/abstract-truth-concept-composition_23-2149051356.jpg?w=1060&t=st=1693108610~exp=1693109210~hmac=669e8a48a53090e88fabb64f36b3610261b3148beb272b3d8d48a37bc958be59"
              class="rounded-shaped"></v-img>
          </div>
        </v-col>
        <v-col cols="8">
          <h3 class="text-body-1 text-left text-primary pb-5">Self-improvement is all forms of efforts, activities or
            actions taken to
            improve self-abilities, interests, talents, potential, self-awareness, skills to quality of life with the aim
            of
            being better than before.</h3>
          <h3 class="text-body-1 text-left text-primary pb-5">In essence, self-improvement is indeed something that has
            become the
            responsibility of the individual. That's because, in improving quality and self-development, it is necessary
            to
            have a will that comes from the individual, not from other people.</h3>
          <h3 class="text-body-1 text-left text-primary">Self-improvement that is applied in everyday life will certainly
            produce
            benefits for the individual. Self improvement in the individual will certainly affect himself. He did this as
            an
            effort to explore his potential and develop himself so that he would not live in the same life.</h3>
        </v-col>
      </v-row>
    </div>

    <div>

      <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 mb-16 text-primary">Books</h1>

      <v-row>
        <v-col cols="3" v-for="book in books" :key="book.title">
          <v-hover v-slot:default="{ isHovering, props }">
            <v-card v-bind="props" :loading="loading" @click="reserve" class="mx-auto my-12 bg-tertiary">
              <template v-slot:loader="{ isActive }">
                <v-progress-linear :active="isActive" color="deep-purple" height="4" indeterminate></v-progress-linear>
              </template>

              <v-img cover height="250" :src="book.src">
                <v-expand-transition>
                  <div v-if="isHovering"
                    class="d-flex transition-fast-in-fast-out bg-secondary v-card--reveal text-h2 text-uppercase"
                    style="height: 100%;">
                    <a class="text-decoration-none text-quarternary" :href="book.order" target="_blank">Order</a>
                  </div>
                </v-expand-transition>
              </v-img>

              <v-card-item class="text-uppercase">
                <v-card-title class="text-primary" v-text="book.title"></v-card-title>

                <v-card-subtitle>
                  <span class="me-1 text-primary" v-text="book.author"></span>
                </v-card-subtitle>
              </v-card-item>

              <v-card-text>
                <v-row align="center" class="mx-0 mb-4">
                  <v-rating :model-value="book.rate" color="primary" density="compact" half-increments readonly
                    size="small"></v-rating>

                  <div class="text-primary ms-2" v-text="book.rate"></div>
                </v-row>

                <div class="text-primary" v-text="book.description"></div>
              </v-card-text>
            </v-card>
          </v-hover>
        </v-col>
      </v-row>

    </div>

  </v-responsive>
</template>

<script setup>
import { ref } from "vue";

const books = ref([
  {
    title: 'Sukarno: Biografi Lengkap Negarawan Sejati',
    src: 'https://cdn.gramedia.com/uploads/items/9786025448942_Sukarno--Biografi-Lengkap-Negarawan-Sejati.jpg',
    rate: 4.6,
    author: 'Anom Whani Wicaksana',
    description: 'This book summarizes Sukarnos life journey from childhood to death and attempts to establish Sukarno as a complete human being. In addition, this book is written in an easy-to-understand.',
    order: 'https://shopee.co.id/product/581413035/16119723009?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4mY8ldauENLJ7Zd-Hp9mR4nNRZDMuWJdeaxem2hmK1MWHUMY6UiiX8aAlI7EALw_wcB'
  },

  {
    title: 'Biografi A.R. Baswedan, Membangun Bangsa, Merajut Keindonesiaan',
    src: 'https://cdn.gramedia.com/uploads/items/45288/thumb_image_normal/ID_BARBMB2018MTH12.jpg',
    rate: 4.3,
    author: 'Suratmin dan Didi Kwartanada',
    description: 'Semarang, August 1, 1934. The newspaper of the Peranakan Chinese group, Mata Hari, published a shocking photo of a young man of Arab descent wearing a beskap and belangkon!',
    order: 'https://shopee.co.id/product/822907480/17297735053?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4lMK6n8qTJeGqe6j1N-tplr8HoQ4ieQUbpp0McvE1bVlfrKQewBCwIaAgs1EALw_wcB'
  },

  {
    title: 'Tan Malaka : Biografi Singkat 1897 - 1949',
    src: 'https://cdn.gramedia.com/uploads/items/TANMALAKA.jpg',
    rate: 4.5,
    author: 'Taufik Adi Susilo',
    description: 'Tan Malaka is an example of a militant, radical, and revolutionary revolutionary figure. But unfortunately, his name and role in Indonesian independence were deliberately obscured.',
    order: 'https://shopee.co.id/product/29863831/5062925511?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4m_Dx8pABWxNsShCEJmp1AKvIs4S88aMngjyuOjpJpVAHMCRG-PM4kaAuIzEALw_wcB'
  },

  {
    title: 'Biografi Politik Habibie : Dari Malari Sampai Reformasi',
    src: 'https://cdn.gramedia.com/uploads/items/9789799116048_biografi-politik-habibie-dari-malari-sampai-reformasi.jpg',
    rate: 5,
    author: 'Raden Toto Sugiharto',
    description: 'Habibies political career began when he answered President Soehartos call home during the frenzy of the Malari incident in 1974.',
    order: 'https://shopee.co.id/product/109666890/4252341353?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4mq7Cxi1nrRyeIFF0-0GQu3WrYeCGuSv56N6njefOwcUCnTgW6mhJcaAs9JEALw_wcB'
  },

  {
    title: 'K.H. Ahmad Dahlan : Biografi Singkat 1868-1923',
    src: 'https://cdn.gramedia.com/uploads/items/9786237219644.jpg',
    rate: 4.3,
    author: 'Adi Nugroho',
    description: '"Dont consider it a small matter, Muhammadiyah is big...", this is one of the statements of K.H. Ahmad Dahlan, written in the book Short Biography (1869-1923) K.H. Ahmad Dahlan.',
    order: 'https://shopee.co.id/product/29863831/6362937298?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4nvj8Ga6nY4e6e0JVeDvbKbuchecTI1acnSGijDgXc0-ZAiFKX73hEaAnNFEALw_wcB'
  },

  {
    title: 'Soe Hok Gie : Biografi Singkat 1942-1969',
    src: 'https://cdn.gramedia.com/uploads/items/9786237219545.jpg',
    rate: 4.1,
    author: 'Muhammad Rifai',
    description: 'Soe Hok Gie came from a house in Kebon Jeruk to become a hero. The spirit of "rebel" was inherited from his father, a Chinese breeder who chose to be a writer and journalist.',
    order: 'https://shopee.co.id/product/61820116/8202691471?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4nsCfcI3CyJizENoGMmYGEeYy_-90CjyGFgVMoVyPScKJP_huneXGIaAgTfEALw_wcB'
  },

  {
    title: 'Mohammad Hatta: Hidup Jujur dan Sederhana untuk Indonesia',
    src: 'https://www.gramedia.com/blog/content/images/2021/08/9786025448225_Mohammad-Hatta.jpg',
    rate: 4.8,
    author: 'Anom whani wicaksana',
    description: 'Together with Sukarno, representing all Indonesian people, he proclaimed the founding of the Republic of Indonesia. Since young, Hatta has shown his ability to lead the organization.',
    order: 'https://shopee.co.id/product/170733618/8170709328?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4mcjcuU32kWoK503yufOI_XA5N27NaLPauuBg839OkzlHceQXWSSbwaAt9SEALw_wcB'
  },

  {
    title: 'K.H. Hasyim Asy`Ari: Biografi Singkat 1871-1947',
    src: 'https://www.gramedia.com/blog/content/images/2021/08/9786237219613-1.jpg',
    rate: 5,
    author: 'Muhammad rivai',
    description: 'KH Hasyim Asyari is a scholar as well as a thinker, fighter and Indonesian national hero. His ideas also colored the struggle for independence, he was the founder of Nahdlatul Ulama, the largest Islamic organization in Indonesia.',
    order: 'https://shopee.co.id/product/29863831/6262933581?gclid=Cj0KCQjwi7GnBhDXARIsAFLvH4ngrTr6HXE4v5EvigSAiMAbLmH6INExy0ysj6M6wYSjDbKYlVeeaPkaAtdNEALw_wcB'
  },

  {
    title: 'Buya Hamka: Sebuah Novel Biografi',
    src: 'https://elibrary.bsi.ac.id/assets/images/buku/222016.jpg',
    rate: 4.6,
    author: 'A.Fuandi',
    description: 'This book tells the life of the former Chairman of the Indonesian Ulema Council (MUI), Buya Hamka. His figure during the Guided Democracy period was someone who disagreed with President Soekarno.',
    order: 'https://www.blibli.com/p/buya-hamka-sebuah-novel-biografi/is--YOB-70008-00750-00001?pickupPointCode=PP-3213229'
  },

  {
    title: 'Gus! Sketsa Seorang Guru Bangsa',
    src: 'https://www.gramedia.com/blog/content/images/2021/08/1--22-.jpg',
    rate: 4.2,
    author: 'Alamsyah M Djafar Wiwit R. Fatkhurrahman',
    description: '',
    order: ''
  },


])
</script>

<script>
export default {
  data: () => ({
    loading: false,
    selection: 1,
  }),

  methods: {
    reserve() {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    },
  },
}
</script>
