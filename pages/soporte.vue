<template>
  <div>
    <HeaderTitulo title="Soporte" />
    <div class="CenteredContent">
      <div class="Frame246">
        <h1 class="textayuda">¿Con qué necesitas ayuda?</h1>
        <div class="Frame217">
          <SearchBar />
          <div class="contacta"><Button buttonText="Contáctanos" /></div>
        </div>
      </div>
      <div class="Line"></div>
      <div class="Frame224">
        <img class="Image59" :src="('/logo.png')" />
        <div class="Frame223">
          <h2>INICIO DE SESIÓN</h2>
          <div class="Frame27">
            <h3>He olvidado mi contraseña.</h3>
            <h3>No he recibido el email de validar la cuenta.</h3>
            <h3>Mi cuenta de correo ya no existe.</h3>

          </div>
        </div>
      </div>
      <div class="Line"></div>
      <h2>MIS JUEGOS</h2>
      <div class="cards">
        <SingleCardGame v-for="game in games" :key="game.id" :game="game" />
      </div>
      <div class="mobile-cards">
        <CardGameMovil
        v-for="game in games"
        :key="game.id"
        :gameId="game.id"
        :gameName="game.name"
        :imageUrl="game.background_image"
      />
      </div>

      <div class="Line"></div>

      <div class="Frame224">
        <img class="Image59" :src="('/logo.png')" />
        <div class="Frame223">
          <h2>COMPRAS</h2>
          <div class="Frame27">
            <h3>¿Cómo puedo obtener un recibo de compra?</h3>
            <h3>¿Qué formas de pago puedo utilizar?</h3>
          </div>
        </div>
      </div>
      <div class="Line"></div>
      <div class="Frame224">
        <img class="Image59" :src="('/logo.png')" />
        <div class="Frame223">
          <h2>MI CUENTA</h2>
          <div class="Frame27">
            <h3>¿Cómo cambio el país en mi cuenta?</h3>
            <h3>¿Cómo cambiar el nombre de vista al público?</h3>
            <h3>Mi cuenta de correo ya no existe.</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from '../components/SearchBar.vue';
import Button from '../components/Button.vue';
import axios from 'axios';
import SwiperComponent from '~/components/SwiperComponent.vue';
import CardGame from '~/components/CardGame.vue';
import SingleCardGame from '~/components/SingleCardGame.vue';
import HeaderSubtitulo from '~/components/HeaderSubtitulo.vue';

const apiKey = '6ef278bbca324856844d239c28a65278'; // Replace with your RAWG API key

export default {
  components: {
    SwiperComponent,
    CardGame,
    SingleCardGame,
    HeaderSubtitulo,
    SearchBar,
    Button
  },
  data() {
    return {
      games: [],
      highlightGame: {},
      featuredGames: []
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

        const gameDetailsPromises = games.map(game => this.fetchGameDetails(game.id));
        const gamesWithDetails = await Promise.all(gameDetailsPromises);

        this.highlightGame = gamesWithDetails[0];
        this.games = gamesWithDetails;
        this.featuredGames = gamesWithDetails.slice(0, 5).map(game => ({
          image: game.background_image,
          title: game.name,
          genre: game.genre
        }));
      } catch (error) {
        console.error('Error fetching game data:', error);
      }
    },
    async fetchGameDetails(gameId) {
      const gameDetailsUrl = `https://api.rawg.io/api/games/${gameId}?key=${apiKey}`;
      try {
        const gameDetailsResponse = await axios.get(gameDetailsUrl);
        return {
          id: gameId,
          background_image: gameDetailsResponse.data.background_image,
          name: gameDetailsResponse.data.name,
          description: gameDetailsResponse.data.description_raw || 'No description available',
          genre: gameDetailsResponse.data.genres && gameDetailsResponse.data.genres.length > 0 ? gameDetailsResponse.data.genres[0].name : 'Unknown Genre'
        };
      } catch (error) {
        console.error('Error fetching game details:', error);
        return {};
      }
    }
  }
};
</script>

<style scoped>
.CenteredContent {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.Frame246 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 39px;
  display: inline-flex;
}

.textayuda {
  align-self: stretch;
  color: #151615;
  word-wrap: break-word;
}

.Frame217 {
  justify-content: flex-start;
  align-items: center;
  gap: 27px;
  display: inline-flex;
}

.Normal {
  text-align: center;
  color: #151615;
  font-size: 18px;
  font-family: SF Mono;
  font-weight: 400;
  word-wrap: break-word;
}

.Line {
  width: 90%;
  height: 1px;
  background-color: #000;
  margin-top: 20px;
  margin: 3rem;
}

.Frame224 {
  justify-content: flex-start;
  align-items: flex-start;
  gap: 116px;
  display: inline-flex;
}

.Image59 {

  height: 351px;
  border-radius: 34px;
}

.Frame223 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 116px;
  display: inline-flex;
}

.Frame27 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 22px;
  display: flex;
  word-wrap: break-word;
}

.mobile-cards {
  display: none;
}

@media (max-width: 480px) {
  .contacta {
    display: none;
  }

  .Image59 {
    display: none;
  }

  .Frame223 {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 3rem;
    display: inline-flex;
  }

  .Frame27 {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 22px;
    display: flex;
    word-wrap: break-word;
  }

  .mobile-cards {
    margin-left: 36px;
    margin-right: 0px;
    gap: 20px;
    display: flex;
    justify-content: flex-start;
    overflow-x: auto;
    width: 80%;
    white-space: nowrap;
  }
}
</style>
