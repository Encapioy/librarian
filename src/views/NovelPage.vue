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
      <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 text-primary">Novel</h1>
      <v-divider :thickness="3" class="mt-3 mb-16"></v-divider>

      <v-row class="mt-5">
        <v-col cols="4">
          <div class="rounded-shaped pa-1 bg-tertiary">
            <v-img
              src="https://img.freepik.com/free-photo/open-book-with-fairytale-scene_52683-107844.jpg?w=1060&t=st=1693108547~exp=1693109147~hmac=aeddf642c7e2efa02f3dd3b65f90f1540252f6c6bbf470db313b85cc018c3a32"
              class="rounded-shaped"></v-img>
          </div>
        </v-col>
        <v-col cols="8">
          <h3 class="text-body-1 text-left text-primary pb-5">Biographical text is a series of writings that contain the
            history or journey of a person's life. However, you can also write your own resume.</h3>
          <h3 class="text-body-1 text-left text-primary pb-5">This series of writings can be said to be self-biographical
            texts or can also be called autobiography.</h3>
          <h3 class="text-body-1 text-left text-primary pb-5">Self-biography text is writing that contains the life
            journey of the author with a third-person point of view based on the knowledge or narrative of the character
            concerned.</h3>
        </v-col>
      </v-row>
    </div>

    <div>

      <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 mb-16 text-primary">Books</h1>

      <v-row>
        <v-col cols="3" v-for="book in books" :key="book.title">
          <v-hover v-slot:default="{ isHovering, props }">
            <v-card v-bind="props" :loading="loading" @click="reserve" class="mx-auto my-12 bg-tertiary" height="500px">
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
  <FooterHome />
</template>

<script setup>
import FooterHome from '@/components/FooterHome.vue'
import { ref } from "vue";

const books = ref([
  {
    title: 'Fur immer dein ian',
    src: 'https://cdn.gramedia.com/uploads/items/img20220928_15154296.jpg',
    rate: 4.6,
    author: 'Valerie',
    description: 'Is there anything more annoying than hiding feelings in the name of friendship? Close to each other but must maintain a safe distance. So that we love still feel comfortable.',
    order: 'https://shopee.co.id/product/26519475/23419364696?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_BFLurQcWkw0OVE3pvPjt1XKOdza3AFadnAzu1sJmAIjmB0C8T-VMaAv8IEALw_wcB'
  },

  {
    title: 'I think i love you',
    src: 'https://cdn.gramedia.com/uploads/items/I_Think_I_Love_You.jpg',
    rate: 4.5,
    author: 'Cha Mirae',
    description: 'Two handsome men become class stars at Kyunghee University. They are both handsome and class stars. A student named Jennie Park is involved in a conflict with Taehyun.',
    order: 'https://shopee.co.id/product/35578691/17387775119?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_AYRu7DmwN5MuXWNBTJgaXSDO1mpFKJ4WVKKSXqZgQCTvoAiQlaLgaArAREALw_wcB'
  },

  {
    title: 'Where story begin',
    src: 'https://cdn.gramedia.com/uploads/items/9786230035463_cover_where_stories.jpg',
    rate: 4,
    author: 'Wacaku',
    description: 'Where Stories Begin is an anthology of short stories curated by the Elex Media Novel Editor from a competition held by Wacaku. Where Stories Begin presents short stories.',
    order: 'https://shopee.co.id/product/289479316/17686634104?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs8bexp_NZYyZ2WcGNVM6snsK--KjKVfN7xIIwtXdL195Nbqhd73XjsaAmWYEALw_wcB'
  },

  {
    title: 'Ramai yang dulu kita bawa pergi',
    src: 'https://cdn.gramedia.com/uploads/items/img20220923_19351789.jpg',
    rate: 4.3,
    author: 'Suci Berliana',
    description: 'This story is just a flashback of our meeting. A story that I can only describe through a series of words. About all the memories that fill the cavity of the head.',
    order: 'https://shopee.co.id/product/16809896/20579633123?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs9zMIuBt36n058PqUu3wy7a4xbcZ0JKgsNKjEHd5TCkeuAHMMmWZY0aAnyIEALw_wcB'
  },

  {
    title: '172 Days',
    src: 'https://cdn.gramedia.com/uploads/items/172_Days.jpg',
    rate: 5,
    author: 'Nadzira Shafa',
    description: 'Can I continue this life? He is my home and my world. "What should I do now continue with my life?" I whispered in my heart. In an instant my life changed.',
    order: 'https://shopee.co.id/product/330255356/21429925486?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs-3iilD6xIlrbtfhk9pyyfrXapUkuxOXoWvH8rLIMpEo8Pw-xv-qt4aArjJEALw_wcB'
  },

  {
    title: 'Funicula funicula (Before the coffee gets cold)',
    src: 'https://cdn.gramedia.com/uploads/items/9786020651927_Funiculi_Funicula_cov.jpg',
    rate: 4.8,
    author: 'Toshikazu Kawaguchi',
    description: 'In a small alley in Tokyo, there is an old cafe that can take visitors to travel through time. The magic of the cafe attracts a woman who wants to turn back.',
    order: 'https://shopee.co.id/product/397439119/4386470813?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs9_bUsrGqpxh4gwrDMJj4R8FynGgr75LR4kqvzBzVIlUtfcJwcNwwUaAjXMEALw_wcB'
  },

  {
    title: 'Terpikat',
    src: 'https://cdn.gramedia.com/uploads/items/Terpikat.jpg',
    rate: 4,
    author: 'Ghefira Zakhira',
    description: 'This story begins when Aruna accidentally sees Abian and immediately falls in love with the man at first sight. Aruna and Abian have very different characteristics.',
    order: 'https://shopee.co.id/product/414738584/19691268284?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs9m5pYCIjYv0zA8J5B05Brf8YRDLMAMj5_9R5T0CitgTT0EpxCCIQ0aAmUJEALw_wcB'
  },

  {
    title: 'Oh My Savior',
    src: 'https://cdn.gramedia.com/uploads/items/Oh_My_Savior.jpg',
    rate: 4.3,
    author: 'Washashira',
    description: 'Loving a perfect guy like Zidane Hamizan is a challenge as well as luck for Zelda Farzana or who is usually called Zee. A guy who can use all his love languages.',
    order: 'https://shopee.co.id/product/149449964/19511286800?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs8Pc0ljmvW8XQIxMkIctZPs7JMBzott2rWFZ8fhNA5zWpbeIicP0RUaAo7cEALw_wcB'
  },

  {
    title: 'Heartbreak Motel',
    src: 'https://cdn.gramedia.com/uploads/items/heartbreak_motel_cov_a2uK3fK.jpg',
    rate: 4.6,
    author: 'Ika Natassa',
    description: 'In a life that never stops harboring mysteries and hiding meaning, doesnt always provide answers to every question, and time flies—one hour, one moment.',
    order: 'https://shopee.co.id/product/5327186/17974845910?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs8xQTaLG9CwpdHBnvQujuuR6Fl5__x9I__hRif7EkLY0iBjxw2FioQaApM3EALw_wcB'
  },

  {
    title: 'Sagaras',
    src: 'https://cdn.gramedia.com/uploads/items/sagaras.jpeg',
    rate: 5,
    author: 'Tere Liye',
    description: 'Finally. Who are Alis parents is answered in this book. Ali, many years, trying to solve the mystery. Paib and Seli certainly wont leave Ali alone, they are true friends.',
    order: 'https://shopee.co.id/product/88234049/22137840759?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs9TPia3d-91hdXUEXMmqpQBgOcRItE3IMxN3A7LnVpr1zk_U6Cl-j4aAhslEALw_wcB'
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
