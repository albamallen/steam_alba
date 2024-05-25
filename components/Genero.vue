<template>
    <div>
        <div class="btt-label" v-if="gameGenre">
            <div class="label sec-p">{{ gameGenre }}</div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30'; // Replace with your RAWG API key

export default {
  data() {
    return {
      gameGenre: '',
      usedIds: new Set(),
    };
  },
  async mounted() {
    await this.fetchRandomGame();
  },
  methods: {
    async fetchRandomGame() {
      const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=50`; // Fetch a list of 50 games

      try {
        const response = await axios.get(apiUrl);
        const games = response.data.results;

        let randomGame;
        do {
          randomGame = games[Math.floor(Math.random() * games.length)];
        } while (this.usedIds.has(randomGame.id) && this.usedIds.size < games.length);

        this.usedIds.add(randomGame.id);

        // Fetch the detailed game data including description and genres
        const gameDetailsUrl = `https://api.rawg.io/api/games/${randomGame.id}?key=${apiKey}`;
        const gameDetailsResponse = await axios.get(gameDetailsUrl);
        this.gameDescription = gameDetailsResponse.data.description_raw || 'No description available';

        // Extract genres
        const genres = gameDetailsResponse.data.genres.map(genre => genre.name).join(', ');
        this.gameGenre = genres || 'No genre available';
      } catch (error) {
        console.error('Error fetching game data:', error);
      }
    },
  }
};
</script>

<style scoped>
.label {
    color: #151615;
    word-wrap: break-word;
  }
  .btt-label {
  padding: 5px 10px;
  background: white;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
}
</style>
