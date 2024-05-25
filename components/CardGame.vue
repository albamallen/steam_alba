<template>
  <NuxtLink :to="`/gamesdet/${gameId}`">
    <div class="frame">
      <div class="modal-juego">
        <div class="video-container">
          <div class="image-container">
            <img :src="gameImage" alt="Game Image"/>
          </div>
          <div class="labels-div">
              <Genero />
          </div>
        </div>
        <div class="text-container">
          <div class="text-div">
            <div class="nombre-del-juego h3">{{ gameTitle }}</div>
            <div class="new-release sec-text">New release</div>
            <div class="description h5">
              {{ gameDescription }}
            </div>
          </div>
          <div class="btt-div">
            <Button buttonText="13,95€" />
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
          </div>
        </div>
      </div>
    </div>
  </NuxtLink>
</template>

<script>
import axios from 'axios';
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';
import Genero from '../components/Genero.vue';

const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30'; // Replace with your RAWG API key

export default {
  name: 'ModalJuego',
  components: {
    Button,
    ButtonGris,
    Genero
  },
  data() {
    return {
      gameImage: '',
      gameTitle: '',
      gameDescription: '',
      gameId: null,
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

        this.gameId = randomGame.id;
        this.gameImage = randomGame.background_image;
        this.gameTitle = randomGame.name;

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
.frame {
  width: 1728px;
  height: 700px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
.modal-juego {
  width: 1348px;
  padding: 60px;
  background: #151615;
  border-radius: 20px;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 71px;
}
.video-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
}
.image-container {
  align-self: stretch;
  height: 314px;
  border-radius: 22px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}
.image {
  align-self: stretch;
  flex: 1;
}
.labels-div {
  height: 29px;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 10px;
  margin-top: 6rem;
}
.label {
  color: #151615;
  font-size: 16px;
  font-family: 'DM Mono', monospace;
  font-weight: 400;
  word-wrap: break-word;
}
.text-container {
  width: 398px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 71px;
}
.text-div {
  align-self: stretch;
  height: 318px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
}
.nombre-del-juego {
  width: 336px;
  color: #fdfdfd;
  word-wrap: break-word;
  font-family: Roboto;
  font-size: 30px;
  font-weight: 700;
}
.new-release {
  word-wrap: break-word;
}
.description {
  color: #fdfdfd;
  word-wrap: break-word;
  display: -webkit-box;
  -webkit-line-clamp: 6;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
.btt-div {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
}
.btt-primary {
  padding: 10px 20px;
  background: var(--primary);
  border-radius: 45px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.btt-icon-search {
  width: 59px;
  height: 59px;
  padding: 5.9px 11.8px;
  background: #d5d5d5;
  border-radius: 40.71px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.icons {
  width: 30.62px;
  height: 30.62px;
  position: relative;
}
.bounding-box {
  width: 30.62px;
  height: 30.62px;
  background: #d9d9d9;
  position: absolute;
}
.search {
  width: 24.6px;
  height: 24.57px;
  background: #151615;
  position: absolute;
  left: 3.01px;
  top: 3.02px;
}
</style>
