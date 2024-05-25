<template>
    <div>
      <HeaderTitulo title="Tienda" />
      <TiendaNavBar />
      <div class="cards"><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /></div>

    </div>
</template>


<script>
import SingleCardGame from '~/components/SingleCardGame.vue';


export default {
  components: {
    
    SingleCardGame
  }
};
</script>