<template>
    <div class="CardjuegoCategoria">
      <div class="Modalcrearcuenta">
        <div class="Videocontainer">
          <div class="Img">
            <img class="Image59" :src="gameImage" :alt="gameTitle" />
            <div class="BttPrimary">
              <Button :buttonText="botonTexto" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import Button from '@/components/Button.vue'; // Importa tu componente de botón personalizado
  
  export default {
    name: 'CardTipo',
    props: {
      botonTexto: {
        type: String,
        default: 'Género' // Texto por defecto para el botón
      }
    },
    data() {
      return {
        gameImage: '',
        gameTitle: ''
      };
    },
    async mounted() {
      await this.fetchRandomGame();
    },
    methods: {
      async fetchRandomGame() {
        const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30'; // Reemplaza con tu clave de la API de RAWG
        const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=50`; // Obtener una lista de 50 juegos
  
        try {
          const response = await axios.get(apiUrl);
          const games = response.data.results;
  
          const randomGame = games[Math.floor(Math.random() * games.length)];
  
          // Obtener los detalles del juego, incluida la imagen y el título
          const gameDetailsUrl = `https://api.rawg.io/api/games/${randomGame.id}?key=${apiKey}`;
          const gameDetailsResponse = await axios.get(gameDetailsUrl);
  
          this.gameImage = randomGame.background_image;
          this.gameTitle = randomGame.name;
        } catch (error) {
          console.error('Error al obtener los datos del juego:', error);
        }
      }
    },
    components: {
      Button // Registra el componente de botón personalizado
    }
  };
  </script>
  
  <style scoped>
  /* Estilos de tu componente CardTipo */
  </style>
  

  <style scoped>
  .CardjuegoCategoria {
    width: 501px;
    height: 332px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
  }
  
  .Modalcrearcuenta {
    align-self: stretch;
    height: 332px;
    padding: 30px;
    background: #fdfdfd;
    border-radius: 20px;
    border: 3px black solid;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    gap: 20px;
    display: flex;
  }
  
  .Videocontainer {
    align-self: stretch;
    height: 272px;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 20px;
    display: flex;
  }
  
  .Img {
    width: 259px;
    height: 272px;
    border-radius: 22px;
    overflow: hidden;
    border: 1px black solid;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: flex;
    position: relative; /* Para que el botón esté posicionado correctamente */
  }
  
  .Image59 {
    align-self: stretch;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .BttPrimary {
    position: absolute; /* Para posicionar el botón encima de la imagen */
    left: 50%; /* Ajustar el posicionamiento horizontal del botón */
    top: 50%; /* Ajustar el posicionamiento vertical del botón */
    transform: translate(-50%, -50%); /* Centrar el botón */
    padding: 10px 20px;
    justify-content: center;
    align-items: center;
    display: inline-flex;
  }
  
  .Normal {
    color: #151615;
    font-size: 30px;
    font-family: 'Neue Haas Grotesk Text Pro', sans-serif;
    font-weight: 500;
    word-wrap: break-word;
  }
  </style>
  