<template>
    <div class="swiper-container">
      <swiper :slides-per-view="1" :space-between="10" :loop="true" pagination navigation>
        <swiper-slide v-for="(slide, index) in slides" :key="index" class="slide">
          <img :src="slide.image" alt="slide image" class="slide-image"/>
          <div class="overlay">
            <div class="text-container">
              <h2>{{ slide.title }}</h2>
              <p>{{ slide.subtitle }}</p>
              <div class="buttons">
                <button class="price-button">{{ slide.price }}</button>
                <button class="favorite-button"><Icon name="line-md:heart" size="1.5em" color="black"></Icon></button>
              </div>
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </template>
  
  <script>
  import SwiperCore, { Navigation, Pagination } from 'swiper/core';
  import { Swiper, SwiperSlide } from 'swiper/vue';
  import 'swiper/swiper-bundle.css';
  
  SwiperCore.use([Navigation, Pagination]);
  
  export default {
    components: {
      Swiper,
      SwiperSlide
    },
    data() {
      return {
        slides: [
          { image: '/1.jpg', title: 'Slide 1', subtitle: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla nunc velit, eleifend malesuada leo vitae, ornare tempus turpis. Cras interdum augue sit amet ipsum mollis, non euismod nibh cursus. Suspendisse malesuada, velit in luctus lobortis, libero metus dictum metus', price: '$10' },
          { image: '/2.jpg', title: 'Slide 2', subtitle: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla nunc velit, eleifend malesuada leo vitae, ornare tempus turpis. Cras interdum augue sit amet ipsum mollis, non euismod nibh cursus. Suspendisse malesuada, velit in luctus lobortis, libero metus dictum metus', price: '$20' },
          { image: '/3.jpg', title: 'Slide 3', subtitle: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla nunc velit, eleifend malesuada leo vitae, ornare tempus turpis. Cras interdum augue sit amet ipsum mollis, non euismod nibh cursus. Suspendisse malesuada, velit in luctus lobortis, libero metus dictum metus', price: '$30' }
        ]
      };
    }
  };
  </script>
  
  <style scoped>
  .slide {
    position: relative;
    width: 100%;
    height: 750px;
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
    padding: 70px; /* Ajusta el padding según sea necesario */
  }
  
  .text-container {
    background-color: rgba(128, 128, 128, 0.5); /* Gris transparente */
    width: 625px; /* Ancho del cuadro de texto */
    height: 303px; /* Altura del cuadro de texto */
    padding: 20px; /* Ajusta el padding según sea necesario */
    padding-left: 60px;
    padding-right: 60px;
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
  }
  
  .buttons {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 10px;
  }
  
  .price-button, .favorite-button {
    width: 20%;
    padding: 10px;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    text-align: center;
  }
  
  .price-button {
    background-color: #00FF03; /* Verde */
    color: black;
  }
  
  .favorite-button {
    background-color: #E6E6E6; /* Gris */
    color: black;
  }
  </style>
  