   <template>
    <NuxtLink :to="`/gamesdet/${game.id}`" v-if="game.id">
      <div class="Property1Default">
        <div class="Videocontainer">
          <div class="Labelsdiv">
            <div class="btt-genero" v-if="gameGenre">
              <div class="genero sec-p">{{ game.genre }}</div>
            </div>
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
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';
import Genero from '../components/Genero.vue';

export default {
  name: 'SingleCardGame',
  props: {
    game: {
      type: Object,
      required: true
    }
  },
  components: {
    Button,
    ButtonGris,
    Genero
  },
  computed: {
    gameGenre() {
      return this.game.genre ? this.game.genre : 'Unknown Genre';
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
.Property1Default {
  width: 398px;
  height: 820px;
  padding: 30px;
  background: var(--100);
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
  color: var(--700);
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
  color: var(--700);
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
