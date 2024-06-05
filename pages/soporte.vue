<template>
  <div>
    <HeaderTitulo title="Soporte" />
    <div class="CenteredContent">
      <div class="Frame246">
        <h1 class="textayuda">¿Con qué necesitas ayuda?</h1>
        <div class="Frame217">
          <SearchBar />
          <Button buttonText="Contáctanos" />
        </div>
      </div>
      <div class="Line"></div>
      <div class="Frame224">
        <img class="Image59" :src="('/logo.png')" />
        <div class="Frame223">
          <h2>INICIO DE SESIÓN</h2>
          <div class="Frame27">
            <h3>He olvidado mi contraseña.</h3>
            <h3>No he recibido el email de validar la cuenta.</h3>
            <h3>Mi cuenta de correo ya no existe.</h3>

          </div>
        </div>
      </div>
      <div class="Line"></div>
      <div class="Frame224">
        <img class="Image59" :src="('/logo.png')" />
        <div class="Frame223">
          <h2>COMPRAS</h2>
          <div class="Frame27">
            <h3>¿Cómo puedo obtener un recibo de compra?</h3>
            <h3>¿Qué formas de pago puedo utilizar?</h3>
          </div>
        </div>
      </div>
      <div class="Line"></div>
      <div class="Frame224">
        <img class="Image59" :src="('/logo.png')" />
        <div class="Frame223">
          <h2>MI CUENTA</h2>
          <div class="Frame27">
            <h3>¿Cómo cambio el país en mi cuenta?</h3>
            <h3>¿Cómo cambiar el nombre de vista al público?</h3>
            <h3>Mi cuenta de correo ya no existe.</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from '../components/SearchBar.vue';
import Button from '../components/Button.vue';

export default {
  components: {
    SearchBar,
    Button
  },
};
</script>

<style scoped>
.CenteredContent {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.Frame246 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 39px;
  display: inline-flex;
}

.textayuda {
  align-self: stretch;
  color: #151615;
  word-wrap: break-word;
}

.Frame217 {
  justify-content: flex-start;
  align-items: center;
  gap: 27px;
  display: inline-flex;
}

.Normal {
  text-align: center;
  color: #151615;
  font-size: 18px;
  font-family: SF Mono;
  font-weight: 400;
  word-wrap: break-word;
}

.Line {
  width: 90%;
  height: 1px;
  background-color: #000;
  margin-top: 20px;
  margin: 3rem;
}

.Frame224 {
  justify-content: flex-start;
  align-items: flex-start;
  gap: 116px;
  display: inline-flex;
}

.Image59 {

  height: 351px;
  border-radius: 34px;
}

.Frame223 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 116px;
  display: inline-flex;
}

.Frame27 {
  height: 155px;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 22px;
  display: flex;
  word-wrap: break-word;
}
</style>
