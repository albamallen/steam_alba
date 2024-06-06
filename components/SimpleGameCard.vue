   <template>
    <NuxtLink :to="`/gamesdet/${gameId}`">
      <div class="card-juego-titulo">
        <div class="card">
          <div class="btt-genero" v-if="gameGenre">
            <div class="genero sec-p">{{ gameGenre }}</div>
          </div>
          <div class="video-container">
            <div class="img" :style="{ backgroundImage: `url(${gameImage})` }">
              <img class="image" :src="gameImage" alt="Game Image" />
            </div>
          </div>
          <div class="frame-59">
            <Button buttonText="13,95€" />
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" />
            <ButtonGris :showIcon="true" IconName="line-md:heart" />
          </div>
        </div>
        <div class="frame-58">
          <div class="nombre-del-juego">{{ gameTitle }}</div>
        </div>
      </div>
    </NuxtLink>
  </template>

<script>
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';

export default {
  name: 'SimpleGameCard',
  components: {
    Button,
    ButtonGris
  },
  props: {
    gameId: {
      type: Number,
      required: true
    },
    gameImage: {
      type: String,
      required: true
    },
    gameTitle: {
      type: String,
      required: true
    },
    gameGenre: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.card-juego-titulo {
  width: 319px;
  height: auto;
  display: inline-flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 2rem;
}

.card {
  padding: 30px;
  background: var(--100);
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 20px;
}

.video-container {
  align-self: stretch;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 20px;
}

.img {
  width: 259px;
  height: 272px;
  border-radius: 22px;
  overflow: hidden;
  border: 1px solid var(--100);
  display: flex;
  justify-content: center;
  align-items: center;
}

.image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.frame-59 {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
}

.nombre-del-juego {
  color: var(--100);
  font-size: 22px;
  font-family: Roboto, sans-serif;
  font-weight: 500;
  margin-left: 1rem;
  word-wrap: break-word;
  white-space: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  /* number of lines to show */
  -webkit-box-orient: vertical;
}

.genero {
  color: var(--100);
  word-wrap: break-word;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100%;
}

.btt-genero {
  padding: 5px 10px;
  background: var(--700);
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
}

@media (max-width: 480px) {
  .card-juego-titulo{
    display: none;
  }
}
</style>
