<template>
  <div class="InstallPage">
    <div class="Frame237">
      <div class="Frame235">
        <div class="Logo"><img class="Image59" :src="('/logo.png')" /></div>
        <div class="BttA">
          <h1>Instala Steam</h1>
        </div>
      </div>
      <div class="Frame236">
        <h5 class="SteamDescription">Steam es el mejor lugar para jugar, hablar sobre juegos y crearlos.</h5>
        <div class="StatsFrame">
          <div class="StatsBox">
            <h4 class="StatsLabel">Jugando</h4>
            <h3 class="StatsNumber">4,568,790</h3>
          </div>
          <div class="StatsBox">
            <h4 class="StatsLabel">En línea</h4>
            <h3 class="StatsNumber">13,255,986</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from '../components/Button.vue';

export default {
  components: {
    Button
  }
}
</script>

<style scoped>
.InstallPage {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  background: linear-gradient(180deg, #00FF03 0%, #151615 110%);
}

.Frame237 {
  display: flex;
  flex-direction: column;
  gap: 46px;
  padding: 7.5rem 0rem;
}

.Frame235 {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 47px;
}

.Logo {
  width: 213px;
  height: 213px;
}

.BttA {
  width: 582px;
  height: 151px;

  border-radius: 159.21px;
  border: 11.65px #151615 solid;
  display: flex;
  justify-content: center;
  align-items: center;
}

.Frame236 {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 46px;
}

.SteamDescription {
  color: #151615;
}

.StatsFrame {
  display: flex;
  gap: 90px;
}

.StatsBox {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 11px;
}

.StatsLabel {
  color: black;
}

.StatsNumber {
  color: black;
}

@media (max-width: 480px) {
  .BttA {
    width: 90%;
    height: 100px;
    padding: 3rem;
    border-radius: 100px;
    border: 11.65px #151615 solid;
    display: flex;
    justify-content: center;
    align-items: center;
    h1{
      align-items: center;
    }
  }
}
</style>
