   <template>
    <div class="CardjuegoCategoria">
      <nuxt-link :to="{ name: 'tiendaJuegoGenero', params: { genreId: genreId, botonTexto } }">
        <div class="card">
          <div class="Videocontainer">
            <div class="Img">
              <img class="Image" :src="gameImage" :alt="gameTitle" />
              <div class="BttPrimary">
                <Button :buttonText="botonTexto" />
              </div>
            </div>
          </div>
        </div>
      </nuxt-link>
    </div>
  </template>

<script>
import Button from '@/components/Button.vue';

export default {
  name: 'CardTipo',
  props: {
    botonTexto: {
      type: String,
      default: 'Género'
    },
    genreId: {
      type: String,
      required: true
    },
    gameImage: {
      type: String,
      required: true
    },
    gameTitle: {
      type: String,
      required: true
    }
  },
  components: {
    Button
  }
};
</script>

<style scoped>
.CardjuegoCategoria {
  width: 501px;
  height: 332px;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 10px;
  display: inline-flex;
}

.card {
  align-self: stretch;
  width: 500px;
  height: 332px;
  padding: 30px;
  background: var(--700);
  border-radius: 20px;
  border: 3px var(--100) solid;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 20px;
  display: flex;
}

.Videocontainer {
  align-self: stretch;
  height: 272px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  display: flex;
}

.Img {
  width: 259px;
  height: 272px;
  border-radius: 22px;
  overflow: hidden;
  border: 1px var(--100) solid;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  display: flex;
  position: relative;
}

.Image {
  align-self: stretch;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.BttPrimary {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  padding: 10px 20px;
  justify-content: center;
  align-items: center;
  display: inline-flex;
}

@media (max-width: 480px) {
  .card{
    width: 200px;
    height: 200px;
    padding: 0px;
  }
  .Img {
  width: 150px;
  height: 150px;
  border-radius: 22px;
  overflow: hidden;
  border: 1px var(--100) solid;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  display: flex;
  position: relative;
}
.CardjuegoCategoria {
  width: 200px;
  height: 200px;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 10px;
  display: inline-flex;
}
}
</style>
