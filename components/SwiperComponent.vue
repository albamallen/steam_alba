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
            <div class="btt-genero" v-if="gameGenre">
              <div class="genero sec-p">{{ game.genre }}</div>
            </div>
            <div class="buttons">
              <Button buttonText="13,95€" />
              <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" />
              <ButtonGris :showIcon="true" IconName="line-md:heart" />
            </div>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper-bundle.css';
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';
import Genero from '../components/Genero.vue';

export default {
  components: {
    Swiper,
    SwiperSlide,
    Button,
    ButtonGris,
    Genero
  },
  props: {
    slides: {
      type: Array,
      required: true
    }
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
  color: var(--700);
  border-radius: 40px;
}

.buttons {
  margin-top: 20px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.genero {
  color: var(--100);
  word-wrap: break-word;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100%;
}

.btt-genero {
  padding: 5px 10px;
  background: var(--700);
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
}

@media (max-width: 480px) {
  .swiper-container {
    height: 500px;
    width: 470px;
  }
}
</style>
