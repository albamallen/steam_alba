<!-- <template>
  <div class="modal-overlay">
    <div class="modal-wrapper">
      <div class="modal-content">
        <button class="close-button" @click="closeModal">×</button>
        <h2>Iniciar Sesión en Steam</h2>
        <div class="form-group">
          <label for="username"></label>
          <input type="text" id="username" v-model="username" placeholder="Usuario">
          <hr class="line">
        </div>
        <div class="form-group">
          <label for="password"></label>
          <input type="password" id="password" v-model="password" placeholder="Contraseña">
          <hr class="line">
        </div>
        <div class="button-group">
          <button @click="login" class="login-button">Login</button>
        </div>
        <div class="button-group">
          <button @click="createAccount" class="create-account-button">Crear cuenta</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    login() {
      // Implementar la lógica de inicio de sesión
      console.log('Usuario:', this.username);
      console.log('Contraseña:', this.password);
      // Limpiar los campos después de iniciar sesión
      this.username = '';
      this.password = '';
      // Cerrar el modal después de iniciar sesión
      this.closeModal();
    },
    closeModal() {
      this.$emit('close');
    },
    createAccount() {
      // Implementar la lógica para crear una nueva cuenta
      console.log('Crear cuenta');
      // Emitir un evento para abrir el modal de registro
      this.$emit('openSignupModal');
    },
    createAccount() {
      this.$emit('openSignupModal');
    }
  
  }
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}

.modal-wrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.modal-content {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  width: 416px; /* Ancho de la ventana */
  height: 508px; /* Altura de la ventana */
  position: relative;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 20px;
  background: transparent;
  border: none;
  cursor: pointer;
}

.form-group {
  margin-bottom: 20px; /* Aumenta el espacio entre los grupos de formulario */
  position: relative; /* Para posicionar la línea correctamente */
}

.label {
  font-weight: bold;
  font-family: 'DM Mono';
}

.input {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-family: 'DM Mono';
}

.line {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: #000;
}

.button-group {
  margin-top: 20px;
}

.login-button{
  width: calc(100% - 20px); /* Resta el espacio del margin */
  margin: 10px; /* Establece el margin */
  padding: 10px 0; /* Ajusta el padding */
  background-color: #00FF03;
  color: #000; /* Texto en negro */
  border: none;
  border-radius: 50px;
  cursor: pointer;
}
.create-account-button {
  width: calc(100% - 20px); /* Resta el espacio del margin */
  margin: 10px; /* Establece el margin */
  padding: 10px 0; /* Ajusta el padding */
  background-color: #E6E6E6;
  color: #000; /* Texto en negro */
  border: none;
  border-radius: 50px;
  cursor: pointer;
}

.login-button:hover{
  border:2px solid #000;
}
.create-account-button:hover {
  background-color: #909090; /* Cambia el color al pasar el mouse */
}
</style> -->


<template>
  <div class="modal-overlay" @click.self="closeModal">
    <div class="modal-wrapper">
      <div class="modal-content">
        <button class="close-button" @click="closeModal">×</button>
        <h2 class="modal-title">Inicia sesión en Steam</h2>
        <div class="form-group">
          <label for="username">Usuario</label>
          <input type="text" id="username" v-model="username" placeholder="Usuario">
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input type="password" id="password" v-model="password" placeholder="Password">
        </div>
        <div class="button-group">
          <button @click="login" class="primary-button">Login</button>
        </div>
        <div class="button-group">
          <button @click="createAccount" class="secondary-button">Crear cuenta</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: ''
    };
  },
  methods: {
    login() {
      // Implementa aquí la lógica de inicio de sesión
      console.log('Usuario:', this.username);
      console.log('Password:', this.password);
      // Limpia los campos después de iniciar sesión
      this.username = '';
      this.password = '';
      // Cierra el modal después de iniciar sesión
      this.closeModal();
    },
    closeModal() {
      this.$emit('close');
    },
    createAccount() {
      // Implementa aquí la lógica para redirigir al usuario a la página de registro
      console.log('Redirigiendo a la página de registro...');
    }
  }
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-wrapper {
  background: #FDFDFD;
  border-radius: 15px;
  border: 2px black solid;
  padding: 40px;
}

.modal-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.close-button {
  align-self: flex-end;
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 24px;
}

.modal-title {
  text-align: center;
  color: #151615;
  font-size: 28px;
  font-family: Neue Haas Grotesk Text Pro;
  font-weight: 500;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  color: #6C6C6C;
  font-size: 16px;
  font-family: SF Mono;
  font-weight: 400;
}

input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.button-group {
  display: flex;
  justify-content: center;
}

.primary-button {
  background: #00FF03;
  color: #151615;
  border: none;
  border-radius: 45px;
  padding: 10px 30px;
  cursor: pointer;
}

.secondary-button {
  background: #E6E6E6;
  color: #6C6C6C;
  border: none;
  border-radius: 41px;
  padding: 10px 30px;
  cursor: pointer;
}
</style>
