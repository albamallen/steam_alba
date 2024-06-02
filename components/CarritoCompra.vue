<template>
    <div v-if="isVisible" class="modal-overlay" @click.self="closeCarrito">
      <div class="modal-carrito">
        <div class="carrito-header">
          <div class="mi-carrito">Mi carrito</div>
          <button class="close-button" @click="closeCarrito">X</button>
        </div>
        <div class="carrito-item">
          <div class="game-image" style="background-image: url('https://via.placeholder.com/160x160');"></div>
          <div class="game-details">
            <div class="game-name">Tomb Raider</div>
            <div class="game-price">13,95€</div>
          </div>
        </div>
        <div class="total-section">
          <div class="total-info">
            <div class="total">Total</div>
            <div class="total-price">13,95€</div>
          </div>
          <div class="pagar-button">
            <div class="pagar-text">Pagar</div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CarritoCompra',
    props: {
      isVisible: {
        type: Boolean,
        required: true
      }
    },
    methods: {
      closeCarrito() {
        this.$emit('close');
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
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: flex-end;
    align-items: flex-start;
    z-index: 1000;
  }
  
  .modal-carrito {
    width: 553px;
    padding: 40px;
    background: #b1b1b1;
    border-radius: 51px;
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
  
  .carrito-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .mi-carrito {
    color: black;
    font-size: 30px;
    font-family: 'Neue Haas Grotesk Text Pro';
    font-weight: 500;
  }
  
  .close-button {
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
  }
  
  .carrito-item {
    display: flex;
    gap: 30px;
    align-items: center;
  }
  
  .game-image {
    width: 160px;
    height: 160px;
    border-radius: 22px;
    overflow: hidden;
    background-size: cover;
    background-position: center;
  }
  
  .game-details {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  .game-name {
    color: black;
    font-size: 16px;
    font-family: 'Neue Haas Grotesk Text Pro';
    font-weight: 500;
  }
  
  .game-price {
    color: black;
    font-size: 16px;
    font-family: 'SF Mono';
    font-weight: 400;
  }
  
  .total-section {
    align-self: stretch;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .total-info {
    display: flex;
    align-items: center;
    gap: 58px;
  }
  
  .total {
    color: black;
    font-size: 30px;
    font-family: 'Neue Haas Grotesk Text Pro';
    font-weight: 500;
  }
  
  .total-price {
    color: black;
    font-size: 22px;
    font-family: 'SF Mono';
    font-weight: 400;
  }
  
  .pagar-button {
    padding: 10px 20px;
    background: #00ff03;
    border-radius: 45px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .pagar-text {
    color: #151615;
    font-size: 30px;
    font-family: 'Neue Haas Grotesk Text Pro';
    font-weight: 500;
  }
  </style>
  