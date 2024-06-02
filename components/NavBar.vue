 <!-- <template>
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
          <div class="profile-menu-wrapper">
            <ButtonGris :showIcon="true" IconName="line-md:account" @click="toggleProfileMenu"/>
            <div v-if="showProfileMenu" class="profile-menu">
              <NuxtLink to="/perfil" class="profile-menu-item">Mi perfil</NuxtLink>
              <NuxtLink to="/tiendaPuntos" class="profile-menu-item">Mis puntos</NuxtLink>
              <div class="profile-menu-item" @click="logout">Cerrar sesión</div>
            </div>
          </div>
        </div>
        
        <LoginModal v-if="showLoginModal" @close="closeLoginModal" />
        
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
      showCarrito: false,
      showProfileMenu: false
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
    },
    toggleProfileMenu() {
      this.showProfileMenu = !this.showProfileMenu; // Alterna la visibilidad del menú de perfil
    },
    goToPoints() {
      // Implementa la lógica para ir a la sección de puntos
      console.log('Ir a Mis Puntos');
    },
    logout() {
      // Implementa la lógica para cerrar sesión
      console.log('Cerrar sesión');
    }
  },
  components: {
    LoginModal,
    Button,
    ButtonGris,
    CarritoCompra // Declara el componente CarritoCompra
  }
};
</script> -->

<!--<template>
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
          <div class="button-container" v-if="!isLoggedIn">
            <div class="button" @click="openLoginModal">Inicia sesión</div>
          </div>
          <div v-else>
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" @click="toggleCarrito"/>
            <div class="profile-menu-wrapper">
              <ButtonGris :showIcon="true" IconName="line-md:account" @click="toggleProfileMenu"/>
              <div v-if="showProfileMenu" class="profile-menu">
                <NuxtLink to="/perfil" class="profile-menu-item">Mi perfil</NuxtLink>
                <NuxtLink to="/tiendaPuntos" class="profile-menu-item">Mis puntos</NuxtLink>
                <div class="profile-menu-item" @click="logout">Cerrar sesión</div>
              </div>
            </div>
          </div>
        </div>
        
        <LoginModal v-if="showLoginModal" @login="handleLogin" @close="closeLoginModal" />
       
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
      showCarrito: false,
      showProfileMenu: false,
      isLoggedIn: false // Estado de autenticación
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
    },
    toggleProfileMenu() {
      this.showProfileMenu = !this.showProfileMenu; // Alterna la visibilidad del menú de perfil
    },
    handleLogin(credentials) {
      const { username, password } = credentials;
      if (username === 'alba.mallen' && password === 'steam') {
        this.isLoggedIn = true; // Marca al usuario como autenticado si las credenciales coinciden
        this.closeLoginModal(); // Cierra el modal de inicio de sesión
      } else {
        alert('Credenciales incorrectas');
      }
    },
    logout() {
      this.isLoggedIn = false; // Cierra sesión del usuario
      this.showProfileMenu = false; // Oculta el menú de perfil
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

.profile-menu-wrapper {
  position: relative;
}

.profile-menu {
  position: absolute;
  top: 100%;
  right: 0;
  font-family: DM mono;
  background: white;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  width: 170px;
  margin-top: 10px;
  z-index: 1000; /* Asegúrate de que el menú está por encima de otros elementos */
}

.profile-menu-item {
  padding: 10px 15px;
  font-family: DM mono;
  cursor: pointer;
  transition: background 0.3s;
}

.profile-menu-item:hover {
  background: #f0f0f0;
}

.profile-menu-item a {
  text-decoration: none;
  color: inherit;
}
</style> -->

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
          <div class="button-container" v-if="!isLoggedIn">
            <div class="button" @click="openLoginModal">Inicia sesión</div>
          </div>
          <div class="buttons-group" v-else>
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall" @click="toggleCarrito"/>
            <div class="profile-menu-wrapper">
              <ButtonGris :showIcon="true" IconName="line-md:account" @click="toggleProfileMenu"/>
              <div v-if="showProfileMenu" class="profile-menu">
                <NuxtLink to="/perfil" class="profile-menu-item">Mi perfil</NuxtLink>
                <NuxtLink to="/tiendaPuntos" class="profile-menu-item">Mis puntos</NuxtLink>
                <div class="profile-menu-item" @click="logout">Cerrar sesión</div>
              </div>
            </div>
          </div>
        </div>
        <!-- Modal de inicio de sesión -->
        <LoginModal v-if="showLoginModal" @login="handleLogin" @close="closeLoginModal" />
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
      showCarrito: false,
      showProfileMenu: false,
      isLoggedIn: false // Estado de autenticación
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
    },
    toggleProfileMenu() {
      this.showProfileMenu = !this.showProfileMenu; // Alterna la visibilidad del menú de perfil
    },
    handleLogin(credentials) {
      const { username, password } = credentials;
      if (username === 'alba.mallen' && password === 'steam') {
        this.isLoggedIn = true; // Marca al usuario como autenticado si las credenciales coinciden
        this.closeLoginModal(); // Cierra el modal de inicio de sesión
      } else {
        alert('Credenciales incorrectas');
      }
    },
    logout() {
      this.isLoggedIn = false; // Cierra sesión del usuario
      this.showProfileMenu = false; // Oculta el menú de perfil
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
}

.navbar-text {
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

.buttons-group {
  display: flex;
  gap: 20px; /* Espacio entre los botones */
  align-items: center;
}

.profile-menu-wrapper {
  position: relative;
}

.profile-menu {
  position: absolute;
  top: 100%;
  right: 0;
  font-family: DM mono;
  background: white;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  width: 170px;
  margin-top: 10px;
  z-index: 1000; /* Asegúrate de que el menú está por encima de otros elementos */
}

.profile-menu-item {
  padding: 10px 15px;
  font-family: DM mono;
  cursor: pointer;
  transition: background 0.3s;
}

.profile-menu-item:hover {
  background: #f0f0f0;
}

.profile-menu-item a {
  text-decoration: none;
  color: inherit;
}
</style>
