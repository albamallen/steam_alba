<template>
  <div class="Modalcrearcuenta">
    <button class="CerrarButton" @click="closeModal">
      <ButtonGris :showIcon="true" IconName="line-md:close" />
    </button>
    <div class="Frame55">
      <h2 class="CrearUnaCuentaEnSteam">Crear una cuenta en Steam</h2>
      <div class="Bttdiv">
        <div class="Textinputsec">
          <input class="sec-p" type="text" id="username" v-model="username" placeholder="Nombre">
        </div>
        <div class="Textinputsec">
          <input class="sec-p" type="text" id="username" v-model="username" placeholder="Nombre de usuario">
        </div>
        <div class="Textinputsec">
          <input class="sec-p" type="text" id="username" v-model="username" placeholder="Correo electrónico">
        </div>
        <div class="Textinputsec">
          <input class="sec-p" type="password" id="password" v-model="password" placeholder="Password">
        </div>
      </div>
    </div>
    <div class="Frame56">
      <div class="Frame57">
        <img src="/logo.png" alt="QR Code" style="width: 170.74px; height: 169px;">
        <p class="textQR">Descárgarte la app escaneando el QR con la cámara de tu móvil</p>
      </div>
      <div class="Frame54">
        <Button buttonText="Crear cuenta" />
        <button @click="emitOpenLogin">
          <ButtonGris :showIcon="false" :showText="true" buttonText="Login" />
        </button>
      </div>
    </div>
  </div>
</template>



<style scoped>
.CerrarButton {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: transparent;
  border: none;
  font-size: 16px;
  cursor: pointer;
}

.Modalcrearcuenta {
  width: 797px;
  height: 522px;
  padding: 40px;
  background: #FDFDFD;
  border-radius: 15px;
  border: 2px black solid;
  justify-content: center;
  align-items: center;
  gap: 71px;
  display: inline-flex;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2000;
}

.Frame55 {
  flex-direction: column;
  justify-content: flex-start;
  gap: 30px;
  display: inline-flex;
}

.CrearUnaCuentaEnSteam {
  text-align: center;
  color: #151615;
  word-wrap: break-word;
}

.Bttdiv {
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  display: flex;
}

.Textinputsec {
  align-self: stretch;
  padding-top: 15px;
  padding-bottom: 15px;
  border-bottom: 1px black solid;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 10px;
  display: inline-flex;
}

.Search {
  color: #6C6C6C;
  font-size: 16px;
  font-family: SF Mono;
  font-weight: 400;
  word-wrap: break-word;
}

.Frame56 {
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 40px;
  display: inline-flex;
}

.Frame57 {
  height: 229px;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 20px;
  display: flex;
}

.Qr {
  width: 170.74px;
  height: 169px;
  position: relative;
}

.textQR {
  align-self: stretch;
  text-align: center;
  color: #151615;
  font-size: 16px;
  font-family: Neue Haas Grotesk Text Pro;
  font-weight: 400;
  word-wrap: break-word;
}

.Frame54 {
  height: 134px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  display: flex;
}

@media (max-width: 480px) {
  .Frame57 {
    display: none;
  }

  .Modalcrearcuenta {
    width: 20rem;
    height: 522px;
    background: #FDFDFD;
    border-radius: 15px;
    border: 2px black solid;
    align-items: center;
    gap: 11px;
    display: flex;
    flex-direction: column;
    transform: translate(-50%, -50%);
    z-index: 2000;
  }

  .Frame55 {
    padding-top: 3rem;
    flex-direction: column;
    justify-content: flex-start;
    gap: 20px;
    display: inline-flex;
  }
}
</style>


<script>
export default {
  data() {
    return {
      nombre: '',
      username: '',
      email: '',
      password: ''
    };
  },
  methods: {
    register() {
      console.log('Nombre:', this.nombre);
      console.log('Nombre de usuario:', this.username);
      console.log('Correo electrónico:', this.email);
      console.log('Contraseña:', this.password);
      this.closeModal();
    },
    closeModal() {
      this.$emit('close');
    },
    emitOpenLogin() {
      this.$emit('openLogin');
    }
  }
};
</script>