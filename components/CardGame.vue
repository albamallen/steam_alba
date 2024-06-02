<template>
  <NuxtLink :to="`/gamesdet/${game.id}`" v-if="game.id">
    <div class="frame">
      <div class="modal-juego">
        <div class="video-container">
          <div class="image-container">
            <img :src="game.background_image" alt="Game Image"/>
          </div>
          <div class="labels-div">
            <div class="btt-genero" v-if="gameGenre">
              <div class="genero sec-p">{{ game.genre }}</div>
            </div>
          </div>
        </div>
        <div class="text-container">
          <div class="text-div">
            <div class="nombre-del-juego h3">{{ game.name }}</div>
            <div class="new-release sec-text">New release</div>
            <div class="description h5" ref="description">{{ game.description }}</div>
          </div>
          <div class="btt-div">
            <Button :buttonText="buttonText" />
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
            <ButtonGris :showIcon="true" IconName="line-md:heart" />
          </div>
        </div>
      </div>
    </div>
  </NuxtLink>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<script>
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';
import Genero from '../components/Genero.vue';

export default {
  name: 'ModalJuego',
  props: {
    game: {
      type: Object,
      required: true
    },
    buttonText: {
            type: String,
            default: '13,95'
        },
  },
  components: {
    Button,
    ButtonGris,
    Genero
  },
  computed: {
    gameGenre() {
      return this.game.genres ? this.game.genres : 'Unknown Genre';
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.limitDescriptionHeight();
    });
  },
  methods: {
    limitDescriptionHeight() {
      const descriptionElement = this.$refs.description;
      const lineHeight = parseInt(window.getComputedStyle(descriptionElement).lineHeight);
      const maxHeight = lineHeight * 6;

      if (descriptionElement.clientHeight > maxHeight) {
        descriptionElement.style.maxHeight = `${maxHeight}px`;
        descriptionElement.style.overflow = 'hidden';
      }
    }
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
  background: var(--100);
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
  color: var(--700);
  word-wrap: break-word;
  font-family: Roboto;
  font-size: 30px;
  font-weight: 700;
}
.new-release {
  word-wrap: break-word;
}
.description {
  color: var(--700);
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
</style>
