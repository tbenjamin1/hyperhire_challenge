<template>
  <div class="q-gutter-md">
    <div class="q-pa-sm row justify-center">
      <!-- Duplicate the first image link 5 times -->
      <MyCard class="my-main-card" v-for="index in 5" :key="'mountains-' + index" :image-src="mountainsImageSrc"
        :avatar-src="avatarSrc" title="Our Changing Planet" author="John Doe" :watch-count="5400" />

      <!-- Duplicate the second image link 2 times -->
      <MyCard class="my-main-card" v-for="index in 2" :key="'parallax1-' + index" :image-src="parallax1ImageSrc"
        :avatar-src="avatarSrc" title="Our Changing Planet" author="John Doe" :watch-count="5400" />

      <!-- Use the third image link once -->
      <MyCard class="my-main-card" :image-src="parallax2ImageSrc" :avatar-src="avatarSrc"
        title="Our Changing Planet Our Changing Planet Our Changing Planet Our Changing Planet" author="John Doe"
        :watch-count="5400" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import MyCard from '../components/MyCard.vue';

export default {
  components: {
    MyCard
  },
  setup() {
    const mountainsImageSrc = 'https://cdn.quasar.dev/img/mountains.jpg';
    const parallax1ImageSrc = 'https://cdn.quasar.dev/img/parallax1.jpg';
    const parallax2ImageSrc = 'https://cdn.quasar.dev/img/parallax2.jpg';
    const avatarSrc = 'https://cdn.quasar.dev/img/avatar.png';

    return {
      mountainsImageSrc,
      parallax1ImageSrc,
      parallax2ImageSrc,
      avatarSrc
    };
  }
};
</script>
