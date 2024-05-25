<!-- <template>
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
              <ButtonGris :showIcon="true" IconName="line-md:plus" />
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

SwiperCore.use([Navigation, Pagination]);

const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30'; // Reemplaza con tu clave de API de RAWG

export default {
  components: {
    Swiper,
    SwiperSlide,
    Icon: () => import('nuxt-icon')
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
      const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=10`; // Obtener 10 juegos

      try {
        const response = await axios.get(apiUrl);
        const games = response.data.results;

        this.slides = games.map(game => ({
          image: game.background_image,
          title: game.name,
          subtitle: game.genres.map(genre => genre.name).join(', '), // Géneros del juego
          price: this.generateRandomPrice()
        }));
      } catch (error) {
        console.error('Error fetching games data:', error);
      }
    },
    generateRandomPrice() {
      const prices = ['$9.99', '$14.99', '$19.99', '$24.99'];
      return prices[Math.floor(Math.random() * prices.length)];
    }
  }
};
</script>

<style scoped>
.swiper-container {
  width: 100%;
  height: 750px;
}

.slide {
  position: relative;
  width: 100%;
  height: 100%;
}

.image-container {
  width: 100%;
  height: 100%;
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
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 70px;
}

.text-container {
  background-color: rgba(128, 128, 128, 0.5);
  width: 625px;
  height: 303px;
  padding: 20px 60px;
  box-sizing: border-box;
  color: white;
  border-radius: 40px;
}

h2 {
  margin: 0;
  font-size: 2em;
}

p {
  margin: 0;
  font-size: 1.2em;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 6; /* Número máximo de líneas */
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
}

.buttons {
  margin-top: 20px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.price-button,
.favorite-button {
  width: 20%;
  padding: 10px;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  text-align: center;
}

.price-button {
  background-color: #00ff03;
  color: black;
}

.favorite-button {
  background-color: #e6e6e6;
  color: black;
}
</style> -->



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
              <ButtonGris :showIcon="true" IconName="line-md:plus" />
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
  width: 100%;
  height: 750px;
}

.slide {
  position: relative;
  width: 100%;
  height: 100%;
}

.image-container {
  width: 100%;
  height: 100%;
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
  width: 100%;
  height: 100%;
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

h2 {
  margin: 0;
  font-size: 2em;
}

p {
  margin: 0;
  font-size: 1.2em;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 6;
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
}

.buttons {
  margin-top: 20px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}
</style>
