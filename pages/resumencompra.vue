<template>
  <div>
    <div class="juegos">
      <CardGame :game="highlightGame" />
      <CardGame :game="highlightGame1" />
    </div>
    <div class="juegomovil">
      <CardMovil :game="highlightGame" />
      <CardMovil :game="highlightGame1" />
    </div>
    <div class="left">
      <HeaderSubtitulo HeadingText="TOTAL a pagar : 27,9€" :showButton="false" :showPuntos="false" :showPagar="true"
        buttonText="REALIZAR COMPRA" />
    </div>
    <HeaderSubtitulo HeadingText="Juegos Relacionados" :showButton="false" :showPuntos="false" :showPagar="false" />
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
  </div>
</template>

<script>
import axios from 'axios';
import SwiperComponent from '~/components/SwiperComponent.vue';
import CardGame from '~/components/CardGame.vue';
import CardMovil from '~/components/CardMovil.vue';
import SingleCardGame from '~/components/SingleCardGame.vue';
import HeaderSubtitulo from '~/components/HeaderSubtitulo.vue';

const apiKey = '6ef278bbca324856844d239c28a65278'; // Replace with your RAWG API key

export default {
  components: {
    SwiperComponent,
    CardGame,
    SingleCardGame,
    HeaderSubtitulo
  },
  data() {
    return {
      games: [],
      highlightGame: {},
      highlightGame1: {},
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
        this.highlightGame1 = gamesWithDetails[1];
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

<style>
.cards {
  margin-left: 80px;
  margin-right: 20px;
  gap: 40px;
  display: flex;
  justify-content: flex-start;
  overflow-x: auto;
  width: calc(100% - 100px);
  white-space: nowrap;
}

.left {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
}
.juegomovil{
  display: none;
}

@media (max-width: 480px) {
  .juegos{
    display: none;
  }
  .juegomovil{
    display: flex;
    flex-direction: column;
  }
}
</style>