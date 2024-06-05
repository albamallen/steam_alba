<!-- <template>
  <div class="Frame247">
    <h1 class="Titulo">{{ title }}</h1>
    <div class="Floatingnav">
      <ButtonGris :showIcon="true" IconName="ic:baseline-language" />
      <div @click="toggleLanguageMenu">
        <ButtonGris :showIcon="true" IconName="ic:baseline-language" />
      </div>
      <div v-if="showLanguageMenu" class="language-menu">
        <ul>
          <li @click="selectLanguage('en')">English</li>
          <li @click="selectLanguage('es')">Español</li>
          <li @click="selectLanguage('fr')">Français</li>
  
        </ul>
      </div>
      <ButtonGris :showIcon="true" IconName="line-md:search" @click="toggleSearchBar" />
      <SearchBar v-if="showSearchBar" @close="toggleSearchBar" />
    </div>

  </div>
</template>

<script>
import SearchBar from './SearchBar.vue';

export default {
  props: {
    title: {
      type: String,
      default: "Titulo" // Si no se proporciona un título, se usará "Titulo" por defecto
    }
  },
  components: {
    SearchBar
  },
  data() {
    return {
      showSearchBar: false
    };
  },
  methods: {
    toggleSearchBar() {
      this.showSearchBar = !this.showSearchBar;
    }
  }
};
</script>

<style scoped>
.Frame247 {
  width: 100%;
  height: 140px;
  justify-content: space-between;
  align-items: center;
  display: inline-flex;
  padding: 42px;
}

.Titulo {
  width: 502px;
  color: var(--100);
  word-wrap: break-word;
}

.Floatingnav {
  padding-left: 45px;
  padding-right: 45px;
  padding-top: 30px;
  padding-bottom: 30px;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 30px;
  display: flex;
  align-items: center;
}

.BttIconLanguage,
.BttIconSearch {
  width: 80px;
  height: 80px;
  padding: 10px 20px;
  background: #D5D5D5;
  border-radius: 41px;
  justify-content: center;
  align-items: center;
  display: flex;
}

.Icons {
  width: 51.90px;
  height: 51.90px;
  position: relative;
}

.BoundingBox {
  width: 51.90px;
  height: 51.90px;
  left: 0px;
  top: 0px;
  position: absolute;
  background: #D9D9D9;
}

.Language,
.Search {
  width: 41.70px;
  height: 41.64px;
  left: 5.10px;
  top: 5.13px;
  position: absolute;
  background: var(--100);
}

.SearchBar {
  position: absolute;
  top: 140px;
  right: 45px;
  z-index: 999;
  /* Asegúrate de que el z-index sea mayor que cualquier otro elemento para que aparezca encima */
}
</style> -->


<template>
  <div class="Frame247">
    <h1 class="Titulo">{{ title }}</h1>
    <div class="Floatingnav">
      <div class="icon-wrapper" @click="toggleLanguageMenu">
        <ButtonGris :showIcon="true" IconName="ic:baseline-language" />
        <div v-if="showLanguageMenu" class="language-menu">
          <ul>
            <li class="sec-p" @click="selectLanguage('en')">English</li>
            <li class="sec-p" @click="selectLanguage('es')">Español</li>
            <li class="sec-p" @click="selectLanguage('fr')">Français</li>
            <!-- Agrega más idiomas según sea necesario -->
          </ul>
        </div>
      </div>
      <ButtonGris :showIcon="true" IconName="line-md:search" @click="toggleSearchBar" />
      <SearchBar v-if="showSearchBar" @close="toggleSearchBar" />
    </div>
  </div>
</template>



<script>
import SearchBar from './SearchBar.vue';
import ButtonGris from '../components/ButtonGris.vue';

export default {
  components: {
    SearchBar,
    ButtonGris
  },
  props: {
    title: {
      type: String,
      default: "Titulo" // Si no se proporciona un título, se usará "Titulo" por defecto
    }
  },
  data() {
    return {
      showSearchBar: false,
      showLanguageMenu: false
    };
  },
  methods: {
    toggleSearchBar() {
      this.showSearchBar = !this.showSearchBar;
    },
    toggleLanguageMenu() {
      this.showLanguageMenu = !this.showLanguageMenu;
    },
    selectLanguage(language) {
      console.log('Selected language:', language);
      // Aquí puedes agregar la lógica para cambiar el idioma si es necesario
      this.showLanguageMenu = false; // Cierra el menú después de seleccionar un idioma
    }
  }
};
</script>

<style scoped>
.Frame247 {
  width: 100%;
  height: 140px;
  justify-content: space-between;
  align-items: center;
  display: inline-flex;
  padding: 42px;
}

.Titulo {
  width: 502px;
  color: var(--100);
  word-wrap: break-word;
}

.Floatingnav {
  padding-left: 45px;
  padding-right: 45px;
  padding-top: 30px;
  padding-bottom: 30px;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 30px;
  display: flex;
  align-items: center;
}

.icon-wrapper {
  position: relative;
}

.language-menu {
  position: absolute;
  top: calc(100% + 10px); /* Abajo del icono, ajusta el espacio */
  right: 0;
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  z-index: 1000;
}

.language-menu ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.language-menu li {
  padding: 10px 20px;
  cursor: pointer;
}

.language-menu li:hover {
  background-color: #f0f0f0;
}

.BttIconLanguage,
.BttIconSearch {
  width: 80px;
  height: 80px;
  padding: 10px 20px;
  background: #D5D5D5;
  border-radius: 41px;
  justify-content: center;
  align-items: center;
  display: flex;
}

.Icons {
  width: 51.90px;
  height: 51.90px;
  position: relative;
}

.BoundingBox {
  width: 51.90px;
  height: 51.90px;
  left: 0px;
  top: 0px;
  position: absolute;
  background: #D9D9D9;
}

.Language,
.Search {
  width: 41.70px;
  height: 41.64px;
  left: 5.10px;
  top: 5.13px;
  position: absolute;
  background: var(--100);
}

.SearchBar {
  position: absolute;
  top: 140px;
  right: 45px;
  z-index: 999;
  /* Asegúrate de que el z-index sea mayor que cualquier otro elemento para que aparezca encima */
}
</style>
