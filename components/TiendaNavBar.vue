<template>
    <div class="Righthero">
        <div class="Frame152">
          <NuxtLink to="/tienda" :class="{ 'active': currentPage === '/tienda' }">Nuevos y destacables</NuxtLink>
          <NuxtLink to="/tiendaJuegos" :class="{ 'active': currentPage === '/tiendaJuegos' }">Juegos por tipo</NuxtLink>
          <NuxtLink to="/tiendaOfertas" :class="{ 'active': currentPage === '/tiendaOfertas' }">Ofertas</NuxtLink>
          <NuxtLink to="/tiendaPuntos" :class="{ 'active': currentPage === '/tiendaPuntos' }">Tienda de puntos</NuxtLink>
        </div>
    </div>
  </template>
  
  <script>
  import ButtonGris from '../components/ButtonGris.vue';
  
  export default {
    components: {
      ButtonGris
    },
    data() {
      return {
        currentPage: ''
      };
    },
    mounted() {
      this.currentPage = this.$route.path;
    }
  };
  </script>
  
  <style scoped>
  .Righthero {
    width: 100%;
    padding: 42px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
  }
  
  .Frame151 {
    align-self: stretch;
    height: 127px;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    gap: 30px;
    display: flex;
  }
  
  .Tienda {
    align-self: stretch;
    color: #151615;
    font-size: 40px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
  }
  
  .Frame152 {
    justify-content: flex-start;
    align-items: center;
    gap: 45px;
    display: inline-flex;
  }
  
  .active {
    background: #00FF03;
    border-radius: 41px;
    border: 1px #00FF03 solid;
    padding: .25rem 1rem;
  }
  </style>
  