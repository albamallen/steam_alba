<template>
    <footer class="footer">
      <div class="footer-left">
        <p>For any questions, please contact steam@support.com</p>
        <div class="iconos">
            <div class="user" @click="panelActive = !panelActive"><Icon name="line-md:account" size="2em" color="black"></Icon></div>
            <div class="user" @click="panelActive = !panelActive"><Icon name="line-md:account" size="2em" color="black"></Icon></div>
            <div class="user" @click="panelActive = !panelActive"><Icon name="line-md:account" size="2em" color="black"></Icon></div>
            <div class="user" @click="panelActive = !panelActive"><Icon name="line-md:account" size="2em" color="black"></Icon></div>
            <div class="user" @click="panelActive = !panelActive"><Icon name="line-md:account" size="2em" color="black"></Icon></div>
        </div>
        <p class="footer-rights">@2024 Steam. All rights reserved</p>
      </div>
      <div class="footer-right">
        <div class="columna">
          <h3>Tienda</h3>
          <ul>
            <!-- Aquí colocarías tus 5 opciones de la tienda -->
          </ul>
        </div>
        <div class="columna">
          <h3>Comunidad</h3>
          <ul>
            <!-- Aquí colocarías tus 5 opciones de la comunidad -->
          </ul>
        </div>
        <div class="columna">
          <h3>Soporte</h3>
          <ul>
            <!-- Aquí colocarías tus 5 opciones de soporte -->
          </ul>
        </div>
      </div>
      <div class="politicas">
        <p>Política de Privacidad</p>
        <p>Términos y Condiciones</p>
      </div>
    </footer>
  </template>
  
  <style scoped>
  footer {
    width: 100%;
    height: 520px;
    background-color: #F8F8F8; 
    .footer-rights{
        color: #6c6c6c;
        
    /* Estilos generales del footer */
  }}
  
  .footer-left {
    float: left;
    width: 50%;
    color: var(--primary);
  }
  
  .footer-right {
    float: right;
    width: 50%;
  }
  
  .iconos {
    /* Estilos para los iconos */
  }
  
  .columna {
    float: left;
    width: 33.33%;
  }
  
  .politicas {
    clear: both;
  }
  </style>
  