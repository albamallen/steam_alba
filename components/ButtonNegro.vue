<template>
    <button :class="{ active: isActive }" @click="toggleActive">
      <h4>{{ buttonText }}</h4>
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
    color: var(--100);
    padding: 10px 20px;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    border: 2px solid transparent;
  }
  
  button:hover {
    background-color: transparent;
    border: 2px solid var(--100);
  }
  
  button.active {
    background-color: var(--100);
    border: 2px solid var(--100);
    color: var(--700);
  }
  
  @media (max-width: 480px) {
    button {
      font-size: 12px;
    }
  }
  </style>
  