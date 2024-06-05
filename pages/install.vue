<template>
  <div class="InstallPage">
    <div class="Frame237">
      <div class="Frame235">
        <div class="Logo"><img class="Image59" :src="('/logo.png')" /></div>
        <div class="BttA">
          <div class="Button">Instala Steam</div>
        </div>
      </div>
      <div class="Frame236">
        <div class="SteamDescription">Steam es el mejor lugar para jugar, hablar sobre juegos y crearlos.</div>
        <div class="StatsFrame">
          <div class="StatsBox">
            <div class="StatsLabel">Jugando</div>
            <div class="StatsNumber">4,568,790</div>
          </div>
          <div class="StatsBox">
            <div class="StatsLabel">En línea</div>
            <div class="StatsNumber">13,255,986</div>
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
  background: linear-gradient(180deg, #00FF03 0%, #151615 110%);
}

.Frame237 {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 46px;
  padding: 7.5rem;
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
  padding: 38.83px 77.66px;
  border-radius: 159.21px;
  border: 11.65px #151615 solid;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 38.83px;
}

.Button {
  color: #151615;
  font-size: 50px;
  font-family: Roboto;
  font-weight: 500;
}

.Frame236 {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 46px;
}

.SteamDescription {
  color: #151615;
  font-size: 18px;
  font-family: "Neue Haas Grotesk Text Pro";
  font-weight: 500;
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
  font-size: 22px;
  font-family: "Neue Haas Grotesk Text Pro";
  font-weight: 500;
}

.StatsNumber {
  color: black;
  font-size: 30px;
  font-family: "Neue Haas Grotesk Text Pro";
  font-weight: 500;
}
</style>
