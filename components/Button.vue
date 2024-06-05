<template>
  <button :class="{ active: isActive }" @click="toggleActive">
    {{ buttonText }}
  </button>
</template>

<script>
export default {
  props: {
    buttonText: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      isActive: false
    };
  },
  methods: {
    toggleActive() {
      this.isActive = !this.isActive;
    }
  }
};
</script>

<style scoped>
button {
  background-color: var(--primary);
  color: var(--100);
  padding: 10px 20px;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  border: 2px solid transparent;
}

button:hover {
  background-color: var(--primary);
  border: 2px solid var(--100);
}

button.active {
  background-color: transparent;
  border: 2px solid var(--100);
}

@media (max-width: 480px) {
  button {
    font-size: 12px;
  }
}
</style>
