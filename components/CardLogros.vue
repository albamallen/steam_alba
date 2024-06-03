<template>
    <div class="Property1Default">
      <div class="Modalcrearcuenta">
        <div class="Videocontainer">
            <div class="Img" :style="{ backgroundImage: `url(${gameImage})` }">
              <img class="image" :src="gameImage" alt="Game Image" />
            </div>
        </div>
      </div>
      <div class="Frame192">
        <div class="Frame58">
            <div class="nombre-del-juego">{{ gameTitle }}</div>
        </div>
        <div class="Frame59">
          <div class="LogrosX100">Logros 56-100</div>
        </div>
      </div>
    </div>
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
  .Property1Default {
    width: 319px;
    height: 364px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
  }
  
  .Modalcrearcuenta {
    padding: 30px;
    background: #151615;
    border-radius: 20px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 20px;
    display: flex;
  }
  
  .Videocontainer {
    align-self: stretch;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 20px;
    display: inline-flex;
  }
  
  .Img {
    width: 259px;
    height: 272px;
    border-radius: 22px;
    overflow: hidden;
    border: 1px black solid;
    background-image: url('https://via.placeholder.com/259x272');
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: inline-flex;
  }
  
  .Image59 {
    align-self: stretch;
    flex: 1 1 0;
  }
  
  .Frame192 {
    width: 319px;
    justify-content: space-between;
    align-items: flex-start;
    display: inline-flex;
  }
  
  .Frame58, .Frame59 {
    justify-content: flex-start;
    align-items: center;
    display: flex;
    font-family: Roboto;
  font-size: 18px;
  font-weight: 400;
  word-wrap: break-word;

  }
  
  .CameraGames, .LogrosX100 {
    color: #151615;
    font-size: 18px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
  }
  </style>
  