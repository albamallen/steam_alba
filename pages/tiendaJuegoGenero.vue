<template>
    <div>
      <HeaderTitulo title="Tienda" />
      <TiendaNavBar />
      <HeaderSubtitulo :HeadingText="genreName" :showPuntos="false" :options="firstOptions"/>
      <div class="cards">
        <!-- Aquí puedes agregar el contenido específico de la página -->
        <SingleCardGame />
        <SingleCardGame />
        <SingleCardGame />
        <SingleCardGame />
        <SingleCardGame />
        <SingleCardGame />
        <SingleCardGame />
        <SingleCardGame />
      </div>
    </div>
  </template>
  
  <script>
  import HeaderTitulo from '../components/HeaderTitulo.vue';
  import TiendaNavBar from '../components/TiendaNavBar.vue';
  import HeaderSubtitulo from '../components/HeaderSubtitulo.vue';
  import SingleCardGame from '../components/SingleCardGame.vue'; // Importa el componente necesario
  
  export default {
    components: {
      HeaderTitulo,
      TiendaNavBar,
      HeaderSubtitulo,
      SingleCardGame
    },
    props: {
      genreId: {
        type: String,
        required: true
      },
      genreName: {
        type: String,
        required: true
      }
    },
    data() {
    return {
      firstOptions: [
        { id: 1, text: 'Rol' },
        { id: 2, text: 'Estrategia' },
        { id: 3, text: 'Storytelling' },
        { id: 4, text: 'Indie' },
        { id: 5, text: 'Aventuras' },
        { id: 6, text: 'Arcade' },
        { id: 7, text: 'Individual' },
        { id: 8, text: 'Multijugador' },
        { id: 9, text: 'Online' }
      ]
    };
  }
  };
  </script>
  
  <style scoped>
  .generos {
    background-color: var(--100);
    padding: 2rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  </style>
  
  <style>
.cards{
  margin-left: 80px;
  margin-right: 20px; /* Margen derecho añadido */
  gap: 40px;
  display: flex;
  justify-content: flex-start;
  overflow-x: auto;
  width: calc(100% - 100px); /* Se ajusta el ancho teniendo en cuenta el margen izquierdo y derecho */
  white-space: nowrap;
}
</style>
