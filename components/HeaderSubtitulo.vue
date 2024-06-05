<template>
  <div class="Property1Default">
    <div class="Frame240">
      <div class="Frame245">
        <div class="BttDot"></div>
        <div class="Frame242">
          <h2 :class="{ 'Subtitulo': true }">{{ HeadingText }}</h2>
        </div>
      </div>
      <div v-if="showButton" class="BttIcons">
        <ButtonGris :showIcon="true" IconName="ic:baseline-keyboard-arrow-down" @click="toggleDropdown" />
      </div>
      <div v-if="showDropdown" class="dropdown">
        <ul>
          <li v-for="option in options" :key="option.id" @click="navigateTo(option)" class="sec-p">
            {{ option.text }}
          </li>
        </ul>
      </div>
      <div v-if="showPuntos" class="BttIcons">
        <ButtonGris :showText="true" :buttonText="buttonText" />
      </div>
      <div v-if="showPagar" class="bttPagar">
        <Button :showText="true" :buttonText="buttonText" />
      </div>
    </div>
  </div>
</template>

<script>
import ButtonGris from '../components/ButtonGris.vue';
import Button from '../components/Button.vue';

export default {
  components: {
    ButtonGris,
    Button
  },
  props: {
    buttonText: {
      type: String,
      default: "Default Text"
    },
    HeadingText: {
      type: String,
      default: "Género"
    },
    showButton: {
      type: Boolean,
      default: true
    },
    showPuntos: {
      type: Boolean,
      default: true
    },
    showPagar: {
      type: Boolean,
      default: true
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      showDropdown: false
    };
  },
  methods: {
    toggleDropdown() {
      this.showDropdown = !this.showDropdown;
    },
    navigateTo(option) {
      this.$router.push({ name: 'tiendaJuegoGenero', params: { genreId: option.id, genreName: option.text } });
    }
  }
};
</script>


<style scoped>
.Property1Default {
  width: 100%;
  height: 120.59px;
  padding-top: 61px;
  padding-bottom: 20px;
  padding-left: 80px;
  padding-right: 80px;
  justify-content: flex-start;
  align-items: center;
  gap: 40px;
  display: inline-flex;
}

.Frame240 {
  justify-content: flex-start;
  align-items: center;
  gap: 40px;
  display: flex;
}

.Frame245 {
  align-self: stretch;
  justify-content: flex-start;
  align-items: center;
  gap: 15px;
  display: flex;
}

.BttDot {
  width: 19px;
  height: 19px;
  padding: 5.71px;
  background: var(--primary);
  border-radius: 24.54px;
}

.Frame242 {
  align-self: stretch;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
  display: flex;
}

.Subtitulo {
  color: var(--100);
  font-size: 22px;
  font-family: Neue Haas Grotesk Text Pro;
  font-weight: 500;
  word-wrap: break-word;
}

.BttIcons {
  display: inline-flex;
}

.dropdown {
  position: absolute;
  background: var(--700);
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.dropdown ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.dropdown li {
  padding: 10px 20px;
  cursor: pointer;
}

.dropdown li:hover {
  background-color: #f0f0f0;
}

.bttPagar {
  display: flex;
  justify-content: flex-end;
}
</style>