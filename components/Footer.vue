<template>
    <div class="Footer">
      <div class="Startfooter">
        <div class="Frame63">
          <div class="Endfooter">
            <div class="BttLinkSec">
              <div class="Link">For any questions, please contact steam@support.com</div>
            </div>
          </div>
          <div class="Frame61">
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
            <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/>
          </div>
        </div>
        <div class="Frame62">
          <div class="Textdiv">
            <div class="BttLinkSec">
              <nuxt-link to="/tienda" class="Link">Tienda</nuxt-link>
            </div>
            <div class="Subtext">
              <div class="BttLinkSec">
                <nuxt-link to="/tienda" class="Link">Nuevos y destacables</nuxt-link>
              </div>
              <div class="BttLinkSec">
                <nuxt-link to="/tiendaJuegos" class="Link">Juegos por tipo</nuxt-link>
              </div>
              <div class="BttLinkSec">
                <nuxt-link to="/tiendaOfertas" class="Link">Ofertas</nuxt-link>
              </div>
              <div class="BttLinkSec">
                <nuxt-link to="/tiendaPuntos" class="Link">Tienda de puntos</nuxt-link>
              </div>
            </div>
          </div>
          <div class="Textdiv">
            <div class="BttLinkSec">
              <nuxt-link to="/soporte" class="Link">Soporte</nuxt-link>
            </div>
            <div class="Subtext">
              <div class="BttLinkSec">
                <nuxt-link to="/soporte" class="Link">Inicio sesión</nuxt-link>
              </div>
              <div class="BttLinkSec">
                <nuxt-link to="/soporte" class="Link">Juegos</nuxt-link>
              </div>
              <div class="BttLinkSec">
                <nuxt-link to="/soporte" class="Link">Compras</nuxt-link>
              </div>
              <div class="BttLinkSec">
                <nuxt-link to="/soporte" class="Link">Mis puntos</nuxt-link>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="Frame64">
        <div class="Endfooter">
          <div class="BttLinkSec">
            <div class="Link">Bread</div>
          </div>
          <div class="BttLinkSec">
            <div class="Link">Bread</div>
          </div>
          <div class="BttLinkSec">
            <div class="Link">Bread</div>
          </div>
          <div class="BttLinkSec">
            <div class="Link">Bread</div>
          </div>
        </div>
        <div class="Endfooter">
          <div class="BttLinkSec">
            <div class="Link">@2024 Steam. All rights reserved</div>
          </div>
          <div class="Left">
            <div class="BttLinkSec">
              <div class="Link">Política y privacidad</div>
            </div>
            <div class="BttLinkSec">
              <div class="Link">Términos y condiciones</div>
            </div>
          </div>
        </div>
      </div>
      <div class="Frame65">
        <div class="BttIconSearch">
            <!-- <ButtonGris :showIcon="true" IconName="ic:outline-local-mall"/> -->
        </div>
      </div>
    </div>
  </template>
  

  <script>
  import ButtonGris from '../components/ButtonGris.vue';
  
  export default {
    components: {
      ButtonGris
    },
    name: 'Footer',
  }
  </script>
  

  <style scoped>
  .Footer {
    width: 1728px;
    height: 520px;
    padding: 60px;
    background: #F8F8F8;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 101px;
    display: inline-flex;
  }
  
  .Startfooter {
    align-self: stretch;
    justify-content: space-between;
    align-items: flex-start;
    display: inline-flex;
  }
  
  .Frame63 {
    width: 473px;
    align-self: stretch;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    display: inline-flex;
  }
  
  .Endfooter {
    justify-content: flex-start;
    align-items: flex-start;
    gap: 221px;
    display: inline-flex;
  }
  
  .BttLinkSec {
    padding: 2px;
    justify-content: flex-start;
    align-items: flex-start;
    display: flex;
  }
  
  .Link {
    color: #00FF03;
    font-size: 16px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
  }
  
  .Frame61 {
    justify-content: flex-start;
    align-items: flex-end;
    gap: 10px;
    display: inline-flex;
  }
  
  .BttIcons {
    width: 39.59px;
    height: 39.59px;
    padding-left: 9.90px;
    padding-right: 9.90px;
    padding-top: 4.95px;
    padding-bottom: 4.95px;
    background: #D5D5D5;
    border-radius: 20.29px;
    justify-content: center;
    align-items: center;
    display: flex;
  }
  
  .Icons {
    width: 20.74px;
    height: 20.74px;
    position: relative;
  }
  
  .BoundingBox {
    width: 20.74px;
    height: 20.74px;
    left: 0px;
    top: -0px;
    position: absolute;
    background: #D9D9D9;
  }
  
  .Mail {
    width: 16.99px;
    height: 16.99px;
    left: 1.99px;
    top: 1.92px;
    position: absolute;
  }
  
  .Vector {
    width: 20.74px;
    height: 20.74px;
    position: relative;
  }
  
  .Frame62 {
    justify-content: flex-start;
    align-items: flex-start;
    gap: 60px;
    display: flex;
  }
  
  .Textdiv {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 30px;
    display: inline-flex;
  }
  
  .Subtext {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: flex;
  }
  
  .Frame64 {
    align-self: stretch;
    height: 78px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 30px;
    display: flex;
  }
  
  .Left {
    justify-content: flex-start;
    align-items: flex-start;
    gap: 60px;
    display: flex;
  }
  
  .Frame65 {
    padding: 10px;
    left: 1605px;
    top: 325px;
    position: absolute;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
  }
  
  .Search {
    width: 16.68px;
    height: 16.66px;
    left: 2.04px;
    top: 2.05px;
    position: absolute;
    background: var(--100);
  }
  </style>
  