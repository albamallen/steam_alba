<template>
  <div>
    <HeaderTitulo title="Tienda" />
    <TiendaNavBar />
    <HeaderSubtitulo HeadingText="Populares" :showPagar="false" :showButton="false" :showPuntos="false" />
    <div class="cards">
      <SimpleGameCard v-for="game in games" :key="game.id" :gameId="game.id" :gameImage="game.background_image"
        :gameTitle="game.name" :gameGenre="game.genre" />
    </div>
    <HeaderSubtitulo HeadingText="Próximamente" :showPagar="false" :showButton="false" :showPuntos="false" />
    <div class="cards">
      <SimpleGameCard v-for="game in upcomingGames" :key="game.id" :gameId="game.id" :gameImage="game.background_image"
        :gameTitle="game.name" :gameGenre="game.genre" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderTitulo from '~/components/HeaderTitulo.vue';
import TiendaNavBar from '~/components/TiendaNavBar.vue';
import HeaderSubtitulo from '~/components/HeaderSubtitulo.vue';
import SimpleGameCard from '~/components/SimpleGameCard.vue';

const apiKey = '6ef278bbca324856844d239c28a65278'; // Reemplaza con tu clave de API de RAWG

export default {
  components: {
    HeaderTitulo,
    TiendaNavBar,
    HeaderSubtitulo,
    SimpleGameCard
  },
  data() {
    return {
      games: [],
      upcomingGames: []
    };
  },
  async mounted() {
    await this.fetchGames();
    await this.fetchUpcomingGames();
  },
  methods: {
    async fetchGames() {
      const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=10`;
      try {
        const response = await axios.get(apiUrl);
        this.games = response.data.results.map(game => ({
          id: game.id,
          background_image: game.background_image,
          name: game.name,
          genre: game.genres && game.genres.length > 0 ? game.genres[0].name : 'Unknown Genre'
        }));
      } catch (error) {
        console.error('Error fetching popular games:', error);
      }
    },
    async fetchUpcomingGames() {
      const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=10&dates=2024-06-01,2025-12-31&ordering=-added`;
      try {
        const response = await axios.get(apiUrl);
        this.upcomingGames = response.data.results.map(game => ({
          id: game.id,
          background_image: game.background_image,
          name: game.name,
          genre: game.genres && game.genres.length > 0 ? game.genres[0].name : 'Unknown Genre'
        }));
      } catch (error) {
        console.error('Error fetching upcoming games:', error);
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
</style>
