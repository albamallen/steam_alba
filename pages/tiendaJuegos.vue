<template>
    <div>
      <HeaderTitulo title="Tienda" />
      <TiendaNavBar />
      <HeaderSubtitulo HeadingText="Géneros" :showPuntos="false" :options="firstOptions"/>
      <div class="generos">
        <CardTipo botonTexto="Rol" genreId="1" genreName="Rol" />
        <CardTipo botonTexto="Estrategia" genreId="2" genreName="Estrategia" />
        <CardTipo botonTexto="Storytelling" genreId="3" genreName="Storytelling" />
        <CardTipo botonTexto="Indie" genreId="4" genreName="Indie" />
        <CardTipo botonTexto="Aventuras" genreId="5" genreName="Aventuras" />
        <CardTipo botonTexto="Arcade" genreId="6" genreName="Arcade" />
      </div>
      <HeaderSubtitulo HeadingText="Tipos de juego" :showPuntos="false" :options="secondOptions"/>
      <div class="generos">
        <CardTipo botonTexto="Individual" genreId="7" genreName="Individual" />
        <CardTipo botonTexto="Multijugador" genreId="8" genreName="Multijugador" />
        <CardTipo botonTexto="Online" genreId="9" genreName="Online" />
      </div>
    </div>
  </template>
  
  <script>
  import HeaderSubtitulo from '../components/HeaderSubtitulo.vue';
  
  export default {
    components: {
      HeaderSubtitulo
    },
    data() {
      return {
        firstOptions: [
          { id: 1, text: 'Rol' },
          { id: 2, text: 'Estrategia' },
          { id: 3, text: 'Storytelling' },
          { id: 4, text: 'Indie' },
          { id: 5, text: 'Aventuras' },
          { id: 6, text: 'Arcade' }
        ],
        secondOptions: [
          { id: 7, text: 'Individual' },
          { id: 8, text: 'Multijugador' },
          { id: 9, text: 'Online' }
        ]
      };
    }
  };
  </script>
  
  <style>
  .generos {
    background-color: var(--100);
    padding: 2rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  </style>
  
