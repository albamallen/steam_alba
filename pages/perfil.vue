<template>
  <div>
    <div class="Frame202-container">
      <div class="Frame158">
        <div class="Frame160">
          <div class="Img">
            <img :src="('/logo.png')" />
          </div>
        </div>
      </div>
      <div class="Frame208">
        <div class="Frame201">
          <h2 class="NombreDeUsuario">Nombre de usuario</h2>
          <div class="BttLabel">
            <div class="Label">500 pts</div>
          </div>
        </div>
        <div class="BttPrimary">
          <Button buttonText="Editar perfil" />
        </div>
      </div>
    </div>
    <HeaderSubtitulo HeadingText="Actividad reciente" :showPagar="false" :showButton="false" :showPuntos="false" />
    <div class="cards">
      <CardLogros v-for="game in games" :key="game.id" :gameId="game.id" :gameImage="game.background_image"
        :gameTitle="game.name" />
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
    <HeaderSubtitulo HeadingText="Lista de deseos" :showPagar="false" :showButton="false" :showPuntos="false" />
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
    <HeaderSubtitulo HeadingText="Mis amigos" :showPagar="false" :showButton="false" :showPuntos="false" />
    <div class="cards-users">
      <User v-for="(user, index) in users" :key="index" :user="user" />
    </div>
    <HeaderSubtitulo HeadingText="Mis juegos" :showPagar="false" :showButton="false" :showPuntos="false" />
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
import User from '~/components/User.vue';
import CardLogros from '~/components/CardLogros.vue'; // Asegúrate de importar tus componentes necesarios
import SingleCardGame from '~/components/SingleCardGame.vue';
import HeaderSubtitulo from '~/components/HeaderSubtitulo.vue';

const apiKey = '6ef278bbca324856844d239c28a65278';

export default {
  components: {
    User,
    CardLogros,
    SingleCardGame,
    HeaderSubtitulo
  },
  data() {
    return {
      games: [],
      users: []
    };
  },
  async mounted() {
    await this.fetchGames();
    await this.fetchUsers();
  },
  methods: {
    async fetchGames() {
      const apiUrl = `https://api.rawg.io/api/games?key=${apiKey}&page_size=10`;
      try {
        const response = await axios.get(apiUrl);
        const games = response.data.results;

        const gameDetailsPromises = games.map(game => this.fetchGameDetails(game.id));
        const gamesWithDetails = await Promise.all(gameDetailsPromises);

        this.games = gamesWithDetails;
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
    },
    async fetchUsers() {
      try {
        const response = await axios.get('https://fakestoreapi.com/users');
        this.users = response.data;
      } catch (error) {
        console.error('Error fetching user data:', error);
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
  justify-content: center;
  align-items: center;
  gap: 10px;
  display: flex;
}

.Frame160 {
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
  flex-direction: column;
  justify-content: center;
  align-items: center;
  display: flex;
}

.Frame208 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 51px;
  display: inline-flex;
  margin-left: 3rem;
}

.Frame201 {
  gap: 4rem;
  justify-content: space-between;
  align-items: center;
  display: inline-flex;
}

.NombreDeUsuario {
  color: black;
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

.cards-users {
  margin-left: 80px;
  margin-right: 20px;
  gap: 40px;
  display: flex;
  justify-content: flex-start;
  overflow-x: auto;
  width: calc(100% - 100px);
  white-space: nowrap;
}

@media (max-width: 480px) {
  .cards {
    display: none;
  }

  .Frame202-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 1rem;
  }

  .Img {
    width: 100px;
    height: 100px;
    border-radius: 204px;
    overflow: hidden;
    border: 3px black solid;
    flex-direction: column;
    display: flex;
  }

  .Frame208 {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
    margin-left: 1rem;
  }

  .Frame201 {
    justify-content: space-between;
    align-items: center;
    display: inline-flex;
    padding: 1rem;
  }
  .cards-users {
  margin-left: 36px;
  margin-right: 0px;
  gap: 40px;
  display: flex;
  justify-content: flex-start;
  overflow-x: auto;
  width: 85%;
  white-space: nowrap;
}

}
</style>
