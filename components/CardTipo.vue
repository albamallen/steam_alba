   <template>
    <div class="CardjuegoCategoria">
      <nuxt-link :to="{ name: 'tiendaJuegoGenero', params: { genreId: genreId, genreName: botonTexto } }">
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
import Button from '@/components/Button.vue'; // Importa tu componente de botón personalizado

export default {
  name: 'CardTipo',
  props: {
    botonTexto: {
      type: String,
      default: 'Género' // Texto por defecto para el botón
    },
    genreId: {
      type: String,
      required: true // El ID del género
    },
    gameImage: {
      type: String,
      required: true // URL de la imagen del juego
    },
    gameTitle: {
      type: String,
      required: true // Título del juego
    }
  },
  components: {
    Button // Registra el componente de botón personalizado
  }
};
</script>

<style scoped>
/* Estilos de tu componente CardTipo */
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
  /* Para que el botón esté posicionado correctamente */
}

.Image {
  align-self: stretch;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.BttPrimary {
  position: absolute;
  /* Para posicionar el botón encima de la imagen */
  left: 50%;
  /* Ajustar el posicionamiento horizontal del botón */
  top: 50%;
  /* Ajustar el posicionamiento vertical del botón */
  transform: translate(-50%, -50%);
  /* Centrar el botón */
  padding: 10px 20px;
  justify-content: center;
  align-items: center;
  display: inline-flex;
}
</style>
