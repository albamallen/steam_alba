<!-- pages/index.vue -->
<template>
  <div>
    <SwiperComponent />
    <CardGame />
    <HeaderSubtitulo HeadingText="Juegos destacados" :showButton="false" :showPuntos="false"/>
    <div class="cards"><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /></div>
  </div>
</template>

<script>
import SwiperComponent from '~/components/SwiperComponent.vue';
import SingleCardGame from '~/components/SingleCardGame.vue';


export default {
  components: {
    SwiperComponent,
    SingleCardGame
  }
};
</script>


<style>
.cards{
  margin-left: 80px;
  gap: 40px;
  display: flex;
  justify-content: space-between;
}
</style>
