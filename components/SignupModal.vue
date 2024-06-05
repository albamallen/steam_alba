<!-- <template>
    <div class="modal-overlay">
      <div class="modal-wrapper">
        <div class="modal-content">
          <button class="close-button" @click="closeModal">×</button>
          <h2>Crear cuenta en Steam</h2>
          
          <div class="form-group">
            <label for="nombre">Nombre:</label>
            <input type="text" id="nombre" v-model="nombre" placeholder="Nombre">
            <hr class="line">
          </div>
          <div class="form-group">
            <label for="username">Nombre de usuario:</label>
            <input type="text" id="username" v-model="username" placeholder="Nombre de usuario">
            <hr class="line">
          </div>
          <div class="form-group">
            <label for="email">Correo electrónico:</label>
            <input type="email" id="email" v-model="email" placeholder="Correo electrónico">
            <hr class="line">
          </div>
          <div class="form-group">
            <label for="password">Contraseña:</label>
            <input type="password" id="password" v-model="password" placeholder="Contraseña">
            <hr class="line">
          </div>
          <div class="button-group">
            <button @click="register" class="login-button">Crear cuenta</button>
          </div>
          <div class="button-group">
            <button @click="closeModal" class="create-account-button">Login</button>
          </div>
        </div>
      </div>
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        nombre: '',
        username: '',
        email: '',
        password: ''
        // Más datos de registro
      }
    },
    methods: {
      register() {
        // Lógica para crear la cuenta
        console.log('Nombre:', this.nombre);
        console.log('Nombre de usuario:', this.username);
        console.log('Correo electrónico:', this.email);
        console.log('Contraseña:', this.password);
        // Más lógica de registro
        // Cerrar el modal después de registrar
        this.closeModal();
      },
      closeModal() {
        this.$emit('close');
      }
    }
  }
  </script>   -->

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
}

.modal-wrapper {
  position: absolute;
}

.modal-content {
  background-color: #fff;
  padding: 20px;
  width: 797px;
  height: 522px;
  border-radius: 10px;
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
  margin-bottom: 20px;
  position: relative;
}

.input {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
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

.login-button {
  width: calc(100% - 20px);
  margin: 10px;
  padding: 10px 0;
  background-color: var(--primary);
  color: #000;
  border: none;
  border-radius: 50px;
  cursor: pointer;
}

.create-account-button {
  width: calc(100% - 20px);
  margin: 10px;
  padding: 10px 0;
  background-color: var(--700);
  color: #000;
  border: none;
  border-radius: 50px;
  cursor: pointer;
}

.create-account-button:hover {
  background-color: #909090;
}
</style>


<template>
  <div class="modal-overlay" style="z-index: 2000;" @click.self="closeModal">
    <div class="modal-wrapper">
      <div class="modal-content">
        <button class="close-button" @click="closeModal">×</button>
        <h2>Crear cuenta en Steam</h2>
        <div class="form-group">
          <label for="nombre">Nombre:</label>
          <input type="text" id="nombre" v-model="nombre" placeholder="Nombre">
          <hr class="line">
        </div>
        <div class="form-group">
          <label for="username">Nombre de usuario:</label>
          <input type="text" id="username" v-model="username" placeholder="Nombre de usuario">
          <hr class="line">
        </div>
        <div class="form-group">
          <label for="email">Correo electrónico:</label>
          <input type="email" id="email" v-model="email" placeholder="Correo electrónico">
          <hr class="line">
        </div>
        <div class="form-group">
          <label for="password">Contraseña:</label>
          <input type="password" id="password" v-model="password" placeholder="Contraseña">
          <hr class="line">
        </div>
        <div class="button-group">
          <button @click="register" class="login-button">Crear cuenta</button>
        </div>
        <div class="button-group">
          <button @click="emitOpenLogin" class="create-account-button">Login</button>
        </div>
      </div>
    </div>
  </div>
</template>

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