<template>
    <div class="Frame202-container">
      <div class="Frame158">
        <div class="Frame160">
          <div class="Img">
            <img class="Image59" :src="('/logo.png')" />
          </div>
        </div>
      </div>
      <div class="Frame208">
        <div class="Frame201">
          <div class="NombreDeUsuario h2">Nombre de usuario</div>
          <div class="BttLabel">
            <div class="Label">500 pts</div>
          </div>
        </div>
        <div class="BttPrimary">
            <Button buttonText="Editar perfil" />
        </div>
      </div>
    </div>
    <HeaderSubtitulo HeadingText="Actividad reciente" :showPagar="false" :showButton="false" :showPuntos="false"/>
    <div class="cards">
      <CardLogros
        v-for="game in games" 
        :key="game.id" 
        :gameId="game.id" 
        :gameImage="game.background_image" 
        :gameTitle="game.name" 
      />
    </div>
    <HeaderSubtitulo HeadingText="Lista de deseos" :showPagar="false" :showButton="false" :showPuntos="false"/>
    <div class="cards">
      <SingleCardGame v-for="game in games" :key="game.id" :game="game" />
    </div>
    <HeaderSubtitulo HeadingText="Mis amigos" :showPagar="false" :showButton="false" :showPuntos="false"/>
    <div class="cards">
      <User v-for="(user, index) in data" :key="index" :user="user" />
    </div>
    <HeaderSubtitulo HeadingText="Mis juegos" :showPagar="false" :showButton="false" :showPuntos="false"/>
    <div class="cards">
      <SingleCardGame v-for="game in games" :key="game.id" :game="game" />
    </div>

  </template>

<script>
import axios from 'axios';
import SwiperComponent from '~/components/SwiperComponent.vue';
import CardGame from '~/components/CardGame.vue';
import SingleCardGame from '~/components/SingleCardGame.vue';
import HeaderSubtitulo from '~/components/HeaderSubtitulo.vue';

const apiKey = '6ef278bbca324856844d239c28a65278'; // Replace with your RAWG API key

const { data } = await useFetch('https://fakestoreapi.com/users', {
        lazy: true,
        server: false,
    })

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
  .Frame202-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.Frame202 {
  width: 940px;
  height: 362px;
  justify-content: space-between;
  align-items: center;
  display: inline-flex;
}
  
  .Frame158 {
    width: 368px;
    height: 362px;
    justify-content: center;
    align-items: center;
    gap: 10px;
    display: flex;
  }
  
  .Frame160 {
    width: 367px;
    height: 361px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    display: inline-flex;
  }
  
  .Img {
    width: 368px;
    height: 361px;
    border-radius: 204px;
    overflow: hidden;
    border: 3px black solid;
    background-image: url(https://via.placeholder.com/368x361);
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: flex;
  }

  .Frame208 {
    width: 529px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 51px;
    display: inline-flex;
  }
  
  .Frame201 {
    width: 515px;
    justify-content: space-between;
    align-items: center;
    display: inline-flex;
  }
  
  .NombreDeUsuario {
    color: black;
    font-size: 40px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
  }
  
  .BttLabel {
    width: 78px;
    height: 26px;
    position: relative;
  }
  
  .Label {
    left: 0px;
    top: 0px;
    position: absolute;
    color: #151615;
    font-size: 16px;
    font-family: SF Mono;
    font-weight: 400;
  }

  </style>
  
