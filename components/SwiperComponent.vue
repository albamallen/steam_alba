<template>
  <div class="swiper-container">
    <swiper :slides-per-view="1" :space-between="10" :loop="true" pagination navigation>
      <swiper-slide v-for="(slide, index) in slides" :key="index" class="slide">
        <div class="image-container">
          <img :src="slide.image" alt="slide image" class="slide-image" />
        </div>
        <div class="overlay">
          <div class="text-container">
            <h1>{{ slide.title }}</h1>
            <Genero />
            <div class="buttons">
              <Button buttonText="13,95€" />
              <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" />
            </div>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
import axios from 'axios';
import SwiperCore, { Navigation, Pagination } from 'swiper/core';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper-bundle.css';
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';

SwiperCore.use([Navigation, Pagination]);

const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30';

export default {
  components: {
    Swiper,
    SwiperSlide,
    Button,
    ButtonGris
  },
  data() {
    return {
      slides: []
    };
  },
  async mounted() {
    await this.fetchGames();
  },
  methods: {
    async fetchGames() {
      const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=10`;

      try {
        const response = await axios.get(apiUrl);
        const games = response.data.results;

        this.slides = games.map(game => ({
          image: game.background_image,
          title: game.name,
        }));
      } catch (error) {
        console.error('Error fetching games data:', error);
      }
    },
  }
};
</script>

<style scoped>
.swiper-container {
  height: 850px;
}

.slide {
  position: relative;
}

.image-container {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.slide-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 70px;
}

.text-container {
  background-color: rgba(128, 128, 128, 0.5);
  padding: 20px 60px;
  box-sizing: border-box;
  color: white;
  border-radius: 40px;
}

.buttons {
  margin-top: 20px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}
</style>
