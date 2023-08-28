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
      <h1 class="text-h3 font-weight-bold text-center text-uppercase mt-16 text-primary">Self Improvement</h1>
      <v-divider :thickness="3" class="mt-3 mb-16"></v-divider>

      <v-row class="mt-5">
        <v-col cols="4">
          <div class="rounded-shaped pa-1 bg-tertiary">
            <v-img
              src="https://img.freepik.com/free-photo/improvement-potential-excellence-diagram-graphic-concept_53876-133936.jpg?w=996&t=st=1693108453~exp=1693109053~hmac=54add6e0612909d9d7627cd8ae073141509115552ae561268d26fce888785851"
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
            <v-card v-bind="props" :loading="loading" @click="reserve" class="mx-auto my-12 bg-tertiary" height="500px">
              <template v-slot:loader="{ isActive }">
                <v-progress-linear :active="isActive" color="deep-purple" height="4" indeterminate></v-progress-linear>
              </template>

              <v-img cover height="250" :src="book.src">
                <v-expand-transition>
                  <div v-if="isHovering"
                    class="d-flex transition-fast-in-fast-out bg-secondary v-card--reveal text-h2 text-uppercase"
                    style="height: 100%;">
                    <a class="text-decoration-none text-quarternary" :href="book.order"
                      target="_blank">Order</a>
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
    title: 'Whats so wrong about your self healing',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Whats_So_Wrong_About_Your_Self_Healing-2023_05_19-10_58_07_547435b8ef05a97b879fab764ee7eca1.jpg',
    rate: 5,
    author: 'Ardhi Mohamad',
    description: 'You have definitely felt anxiety, loneliness, resignation, and sadness before. One of the things that can treat a feeling of slump due to this is self-healing.',
    order: 'https://shopee.co.id/Buku-What%27s-So-Wrong-About-Your-Self-Healing-Ardi-Mohamad-Alvi-Ardhi-Publishing-i.24348221.10268112468'
  },

  {
    title: 'The power of thinking out of the box',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/The_Power_Of_Thinking_Out_Of_The_Box-2023_05_19-10_54_35_6f2ad610a19873d70131ef4ca654f4d9.jpg',
    rate: 4.5,
    author: 'Hasna Wijayati',
    description: 'You must have done some work that required you to think as creatively as possible. With this creative thinking, maybe a solution to the problem at hand will emerge.',
    order: 'https://shopee.co.id/product/904278944/22408328713?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_BkJfzNFHb8i322i17alAXJmJhFAPR1JDVdpnHVEXl1oeqyIRbDuAaAkHVEALw_wcB'
  },

  {
    title: 'A guide book to slow down your life',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/A_Guide_Book_To_Slow_Down_Your_Life-2023_05_19-10_55_16_6b794a67e50899e135c07a8df4a51d5e.jpg',
    rate: 4,
    author: 'Astrid Savitri',
    description: 'Often times in life, a person has gone through and done many things, but still feels empty and feels that its time to change and rearrange their way of life.',
    order: 'https://shopee.co.id/product/24051902/16289580611?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_PGbqpe9ofzrPomAENvlk3MwjlyMxKRizeO2WEHKEY0oBRoqYcDu0aAinFEALw_wcB'
  },

  {
    title: 'Berani tidak disukai',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Berani_Tidak_Disukai-2023_05_19-10_55_55_0c19b4b85ee036e17c4705d647334f74.jpg',
    rate: 4.7,
    author: 'Ichiro Kishimi & Fumitake Koga',
    description: 'This self improvement book outlines the teachings of the 19th century Austrian philosopher, Alfred Adler. This teaching contains how humans should live their lives.',
    order: 'https://shopee.co.id/product/971697938/21780549369?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_v-SyElyGBd0J9bhdo3HC-W9a6oGywGgbhpbI7sV56s3VkS7PF8FIaAk42EALw_wcB'
  },

  {
    title: 'Sebuah seni untuk bersikap bodo amat',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Sebuah_Seni_untuk_Bersikap_Bodo_Amat-2023_05_19-10_58_58_1113bddf22c8eb2498d239b94687287a.png',
    rate: 4.3,
    author: 'Mark Manson',
    description: 'For those of you who easily overthink, feel anxious, and feel afraid, then you need to read this book. The book The Art of Being Totally Ignorant will teach you.',
    order: 'https://shopee.co.id/product/29863831/7363360415?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs85F3QJhlDkI_RLFpDIRvjcY-94RhrRiln6a_fRMzcRJNzbgbG1goIaAgKjEALw_wcB'
  },

  {
    title: 'Merawat luka batin',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Merawat_Luka_Batin-2023_05_19-11_32_47_69fbcb1621b1edd894b35fbea030f2f9.jpg',
    rate: 5,
    author: 'Dr.Jiemi Ardian, Sp.Kj',
    description: 'Inner wounds can be present without you knowing it, just like physical wounds, an injured mind must also be cared for and healed. Not many know how to treat inner wounds.',
    order: 'https://shopee.co.id/product/5219216/16546222106?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_ogYik8HuamIHYQ4UAeu-bR1a78wf0hJP9TB1Vaw29Jh-rU9cmnkAaAgqxEALw_wcB'
  },

  {
    title: 'Tak apa-apa tak sempurna',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Tak_Apa-Apa_Tak_Sempurna-2023_05_19-11_33_28_da97ad56128b6e396e5cf54dd9451c8a.jpg',
    rate: 4.6,
    author: 'Brene Brown',
    description: 'The pressures of life must have been felt by everyone, its just that the portions are different. As humans, some people have also felt that failure is a big problem.',
    order: 'https://shopee.co.id/product/93253702/21945266313?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs_05YjOhZPCWw65CZurr12DWnaHRXhwyM26LatKxM2maA2P_OjW_Y0aAg3_EALw_wcB'
  },

  {
    title: 'Insecurity',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Insecurity_is_My_Middle_Name-2023_05_19-11_34_48_5ed5cec6d0dbe6b00c26f972cd7d77f0.jpg',
    rate: 5,
    author: 'Alvi Syahrin',
    description: 'This is the first self-improvement book written by Alvi Syahrin. Its very successful in making people feel like they are being hugged when they read this book.',
    order: 'https://shopee.co.id/product/5219216/8795521453?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs8oWFutS0ThPcf0lBfzXiVT35UwNdWoQeMEccIHemBytB-v_4rgtwUaAtEJEALw_wcB'
  },

  {
    title: 'Menyakitkan, tapi tak seburuk yang kupikirkan',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/9_Menyakitkan_Tapi_Tak_Seburuk_yang_Kupikirkan-2023_05_19-11_35_35_4c4758cdd632f85963f776010252719f.jpg',
    rate: 4,
    author: 'Lee You-jeong',
    description: 'Painful, But Not as Bad as I Think is a self-improvement book written by Korean writer Lee You-Jeong. This book is suitable for those of you who are facing lifes trials and obstacles.',
    order: 'https://shopee.co.id/product/7186110/8512582646?gclid=Cj0KCQjw6KunBhDxARIsAKFUGs8c6DwIAFKn0rDFOjZF8M6tvy-Uw1DanLlS5j-LM_jv5f2uZle2FOwaAu5sEALw_wcB'
  },

  {
    title: 'Kamu gak sendiri',
    src: 'https://cdn1.katadata.co.id/media/images/temp/2023/05/19/Kamu_Gak_Sendiri-2023_05_19-11_36_23_6ec25cfa904495f7602d41b7679d1193.jpg',
    rate: 4.2,
    author: 'Syahid Muhammad',
    description: 'Youre Not Alone by Syahid Muhammad is a self-improvement book for teenagers who often feel lonely. This 340-page book tries to help its readers not feel alone.',
    order: 'https://shopee.co.id/Buku-Kamu-Gak-Sendiri-(Gradien-Mediatama)-i.7186110.6040165833?sp_atk=0a9b2a73-45f2-444c-8568-037e4bb3c2ae&xptdk=0a9b2a73-45f2-444c-8568-037e4bb3c2ae'
  }


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
