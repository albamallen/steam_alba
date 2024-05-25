<template>
    <NuxtLink :to="`/gamesdet/${game.id}`" v-if="game.id">
      <div class="Property1Default">
        <div class="Videocontainer">
          <div class="Labelsdiv">
            <Genero />
          </div>
          <div class="Img">
            <img class="Image59" :src="game.background_image" alt="Game Image" />
          </div>
        </div>
        <div class="Textcontainer">
          <div class="Textdiv">
            <div class="CameraGames h4">{{ game.name }}</div>
            <div class="NewRelease sec-text">New release</div>
            <div class="Description">{{ game.description }}</div>
          </div>
          <div class="Bttdiv">
            <Button buttonText="13,95€" />
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" />
            <ButtonGris :showIcon="true" IconName="line-md:heart" />
          </div>
        </div>
      </div>
    </NuxtLink>
    <div v-else>
      <p>Loading...</p>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import Button from '../components/Button.vue';
  import ButtonGris from '../components/ButtonGris.vue';
  import Genero from '../components/Genero.vue';
  
  const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30'; // Replace with your RAWG API key
  
  export default {
    name: 'ApiCard',
    components: {
      Button,
      ButtonGris,
      Genero
    },
    data() {
      return {
        game: {}
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
  
          const randomGame = games[Math.floor(Math.random() * games.length)];
  
          // Fetch the detailed game data including description and genres
          const gameDetailsUrl = `https://api.rawg.io/api/games/${randomGame.id}?key=${apiKey}`;
          const gameDetailsResponse = await axios.get(gameDetailsUrl);
  
          this.game = {
            id: randomGame.id,
            background_image: randomGame.background_image,
            name: randomGame.name,
            description: gameDetailsResponse.data.description_raw || 'No description available'
          };
        } catch (error) {
          console.error('Error fetching game data:', error);
        }
      },
    }
  };
  </script>
  
  <style scoped>
.Property1Default {
    width: 398px;
    height: 820px;
    padding: 30px;
    background: #151615;
    border-radius: 20px;
    display: inline-flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    gap: 20px;
}

.Videocontainer {
    align-self: stretch;
    height: 363px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 20px;
}

.Labelsdiv {
    height: 29px;
    display: inline-flex;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
}

.BttLabel {
    padding: 5px;
    background: white;
    color: #151615;
    font-size: 16px;
    font-family: SF Mono;
    font-weight: 400;
}

.Img {
    align-self: stretch;
    height: 314px;
    border-radius: 22px;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
}

.Image59 {
    align-self: stretch;
    width: 100%;
    height: 100%;
    object-fit: cover;
    /* Evita que la imagen se deforme */
}

.Textcontainer {
    align-self: stretch;
    height: 400px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 71px;
}

.Textdiv {
    align-self: stretch;
    height: 250px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
}

.CameraGames {
    width: 336px;
    color: #fdfdfd;
    font-family: Roboto;
    font-size: 22px;
    font-weight: 400;
}

.NewRelease {
    align-self: stretch;
}

.Description {
    align-self: stretch;
    color: #fdfdfd;
    word-wrap: break-word;
    display: -webkit-box;
    -webkit-line-clamp: 6;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
}


.Bttdiv {
    justify-content: center;
    align-items: center;
    gap: 20px;
    display: inline-flex;
}

.BttPrimary {
    padding: 10px 20px;
    background: #00ff03;
    border-radius: 45px;
    color: #151615;
    font-size: 30px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
}

.BttIcons,
.BttIconLikeSmall {
    width: 59px;
    height: 59px;
    padding: 2.92px 5.84px;
    background: #d5d5d5;
    border-radius: 40.71px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.Icons {
    width: 47.32px;
    height: 53.16px;
    position: relative;
}

.LocalMall .BoundingBox,
.Favorite .BoundingBox {
    width: 100%;
    height: 100%;
    position: absolute;
    background: #d9d9d9;
}

.LocalMall .LocalMall,
.Favorite .Favorite {
    position: absolute;
    background: #151615;
}

.LocalMall .LocalMall {
    width: 36.47px;
    height: 40.97px;
    left: 5.86px;
    top: 5.95px;
}

.Favorite .Favorite {
    width: 39.21px;
    height: 44.05px;
    left: 3.76px;
    top: 3.90px;
}
</style>