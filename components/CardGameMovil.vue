<!-- <template>
    <div class="card-amigo">
      <div class="img-container">
        <img class="img" :src="imageUrl" alt="Game Image" />
      </div>
      <div class="frame">
        <div class="title">
          <div class="frame-title">
            <h5 class="nombre-juego">{{ gameName }}</h5>
          </div>
          <div class="frame-icons">
            <ButtonGris :showIcon="true" IconSize="1rem" IconName="ic:outline-local-mall" />
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import ButtonGris from '../components/ButtonGris.vue';
  
  export default {
    name: 'CardGameMovil',
    components: {
      ButtonGris
    },
    props: {
      gameName: {
        type: String,
        default: 'Nombre juego'
      },
      imageUrl: {
        type: String,
        default: 'https://via.placeholder.com/148x70'
      }
    }
  };
  </script>
  
  <style scoped>

  .card-amigo {
    height: 160px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 5px;
    padding: 0rem 1rem;
  }
  
  .img-container {
    width: 148px;
    height: 70px;
    border-radius: 6.27px;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .frame {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 1rem;
  }
  
  .title {
    margin-top: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 19px;
  }
  
  .frame-title {
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }
  
  .nombre-juego {
    color: black;
    font-size: 15px;
  }
  
  .frame-icons {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  </style>
   -->

   <template>
    <NuxtLink :to="`/gamesdet/${gameId}`" v-if="gameId">
      <div class="card-amigo">
        <div class="img-container">
          <img class="img" :src="imageUrl" alt="Game Image" />
        </div>
        <div class="frame">
          <div class="title">
            <div class="frame-title">
              <h5 class="nombre-juego">{{ gameName }}</h5>
            </div>
            <div class="frame-icons">
              <ButtonGris :showIcon="true" IconSize="1rem" IconName="ic:outline-local-mall" />
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
  import ButtonGris from '../components/ButtonGris.vue';
  
  export default {
    name: 'CardGameMovil',
    components: {
      ButtonGris
    },
    props: {
      gameId: {
        type: [String, Number],
        required: true
      },
      gameName: {
        type: String,
        default: 'Nombre juego'
      },
      imageUrl: {
        type: String,
        default: 'https://via.placeholder.com/148x70'
      }
    }
  };
  </script>
  
  <style scoped>
  .card-amigo {
    height: 160px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 5px;
    padding: 0rem 1rem;
  }
  
  .img-container {
    width: 148px;
    height: 70px;
    border-radius: 6.27px;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .frame {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 1rem;
  }
  
  .title {
    margin-top: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 19px;
  }
  
  .frame-title {
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }
  
  .nombre-juego {
    color: black;
    font-size: 15px;
  }
  
  .frame-icons {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  </style>
  