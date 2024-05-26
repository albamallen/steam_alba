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
            <div class="Description" ref="description">{{ game.description }}</div>
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
          
          // Adjust description height after content is loaded
          this.$nextTick(() => {
            this.limitDescriptionHeight();
          });
        } catch (error) {
          console.error('Error fetching game data:', error);
        }
      },
      limitDescriptionHeight() {
        const descriptionElement = this.$refs.description;
        const lineHeight = parseInt(window.getComputedStyle(descriptionElement).lineHeight);
        const maxHeight = lineHeight * 6; // Limit to six lines
  
        if (descriptionElement.clientHeight > maxHeight) {
          descriptionElement.style.maxHeight = `${maxHeight}px`;
          descriptionElement.style.overflow = 'hidden';
        }
      }
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
  
  .NewRelease {
    align-self: stretch;
  }
  
  .CameraGames {
    width: 336px;
    color: #fdfdfd;
    font-family: Roboto;
    font-size: 22px;
    font-weight: 400;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    margin-bottom: 10px;
  }
  
  .Description {
    align-self: stretch;
    color: #fdfdfd;
    word-wrap: break-word;
    overflow: hidden;
    margin-bottom: 20px;
    -webkit-line-clamp: 2;

  }
  
  .Bttdiv {
    justify-content: center;
    align-items: center;
    gap: 20px;
    display: inline-flex;
  }
</style>

  