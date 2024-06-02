<template>
  <div class="navbar">
    <div class="property-wrapper">
      <div class="logo">
        <div class="navbar-left">
          <NuxtLink to="/"><img src="/logo.png" alt="Logo" class="logo"></NuxtLink>
        </div>
      </div>
      <div class="navbar-text">
        <div class="right-nav">
          <div class="button-container">
            <NuxtLink to="/tienda" :class="{ 'nav-link': $route.path !== '/pagina1', 'nav-link-bold': $route.path === '/pagina1' }">Tienda</NuxtLink>
          </div>
          <div class="button-container">
            <NuxtLink to="/soporte" :class="{ 'nav-link': $route.path !== '/pagina1', 'nav-link-bold': $route.path === '/pagina1' }">Soporte</NuxtLink>
          </div>
        </div>
        <div class="left-nav">
          <nuxt-link to="/install">
            <Button buttonText="Instala Steam"/>
          </nuxt-link>
          <div class="button-container">
            <div class="button" @click="openLoginModal">Inicia sesión</div>
          </div>
          <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" @click="toggleCarrito"/>
          <ButtonGris :showIcon="true" IconName="line-md:account"/>
        </div>
        <!-- Modal de inicio de sesión -->
        <LoginModal v-if="showLoginModal" @close="closeLoginModal" />
        <!-- Modal del carrito -->
        <CarritoCompra :isVisible="showCarrito" @close="toggleCarrito"/>
      </div>
    </div>
  </div>
</template>

<script>
import LoginModal from '~/components/LoginModal.vue'; // Importa el componente modal de inicio de sesión
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';
import CarritoCompra from '../components/CarritoCompra.vue'; // Importa el componente CarritoCompra

export default {
  data() {
    return {
      showLoginModal: false,
      showCarrito: false
    };
  },
  methods: {
    openLoginModal() {
      this.showLoginModal = true; // Abre el modal de inicio de sesión al hacer clic en "Iniciar sesión"
    },
    closeLoginModal() {
      this.showLoginModal = false; // Cierra el modal de inicio de sesión
    },
    toggleCarrito() {
      this.showCarrito = !this.showCarrito; // Alterna la visibilidad del carrito
    }
  },
  components: {
    LoginModal,
    Button,
    ButtonGris,
    CarritoCompra // Declara el componente CarritoCompra
  }
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  width: 3.5rem;
  display: flex;
  align-items: center;
}

.property-wrapper {
  display: flex;
  flex-direction: row;
  width: 1728px;
  height: 107px;
  padding: 30px 45px;
  justify-content: space-between;
  align-items: flex-start;
  gap: 45px;
  display: flex;
}

.navbar-text{
  display: flex;
  flex-direction: row;
  gap: 2rem;
}

.right-nav,
.left-nav {
  display: flex;
  gap: 45px;
  align-items: center;
  font-size: 22px;
}

.button-container {
  padding: 10px 20px;
  border-radius: 41px;
  display: flex;
  align-items: center;
}

.button {
  text-align: center;
  color: var(--100);
  font-size: 22px;
  font-family: Roboto;
  font-weight: 500;
  word-wrap: break-word;
  cursor: pointer;
}

.primary-button {
  padding: 10px 20px;
  background: var(--primary);
  border-radius: 45px;
  color: var(--100);
  font-size: 22px;
  font-family: Roboto;
  font-weight: 500;
  word-wrap: break-word;
  cursor: pointer;
}
</style>
