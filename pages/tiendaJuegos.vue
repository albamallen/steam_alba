   <template>
    <div>
      <HeaderTitulo title="Tienda" />
      <TiendaNavBar />
      <HeaderSubtitulo HeadingText="Géneros" :showPagar="false" :showPuntos="false" :options="firstOptions"/>
      <div class="generos">
        <CardTipo v-for="(game, index) in genreGames" 
                  :key="index" 
                  :botonTexto="firstOptions[index].text" 
                  :genreId="firstOptions[index].id"
                  :gameImage="game.background_image" 
                  :gameTitle="game.name" />
      </div>
      <HeaderSubtitulo HeadingText="Tipos de juego" :showPagar="false" :showPuntos="false" :options="secondOptions"/>
      <div class="generos">
        <CardTipo v-for="(game, index) in typeGames" 
                  :key="index" 
                  :botonTexto="secondOptions[index].text" 
                  :genreId="secondOptions[index].id"
                  :gameImage="game.background_image" 
                  :gameTitle="game.name" />
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import HeaderTitulo from '../components/HeaderTitulo.vue';
  import TiendaNavBar from '../components/TiendaNavBar.vue';
  import HeaderSubtitulo from '../components/HeaderSubtitulo.vue';
  import CardTipo from '../components/CardTipo.vue';
  
  const apiKey = '6ef278bbca324856844d239c28a65278'; // Reemplaza con tu clave de API de RAWG
  
  export default {
    components: {
      HeaderTitulo,
      TiendaNavBar,
      HeaderSubtitulo,
      CardTipo
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
        ],
        genreGames: [],
        typeGames: []
      };
    },
    async mounted() {
      await this.fetchRandomGames();
    },
    methods: {
      async fetchRandomGames() {
        const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=50`;
        try {
          const response = await axios.get(apiUrl);
          const games = response.data.results;
  
          // Seleccionar 9 juegos aleatorios
          const randomGames = [];
          for (let i = 0; i < 9; i++) {
            const randomIndex = Math.floor(Math.random() * games.length);
            randomGames.push(games[randomIndex]);
          }
  
          // Asignar 6 juegos a genreGames y 3 juegos a typeGames
          this.genreGames = randomGames.slice(0, 6);
          this.typeGames = randomGames.slice(6, 9);
        } catch (error) {
          console.error('Error al obtener los datos del juego:', error);
        }
      }
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
  