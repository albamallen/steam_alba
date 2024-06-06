<template>
  <div class="Footer">
    <div class="Startfooter">
      <div class="Frame63">
        <div class="Endfooter">
          <div class="BttLinkSec">
            <p class="Link">For any questions, please contact steam@support.com</p>
          </div>
        </div>
        <div class="Frame61">
          <ButtonGris :showIcon="true" IconName="streamline:computer-logo-facebook-2-media-facebook-social" />
          <ButtonGris :showIcon="true" IconName="streamline:computer-logo-google-media-google-social" />
          <ButtonGris :showIcon="true" IconName="streamline:adobe" />
          <ButtonGris :showIcon="true" IconName="streamline:android" />
          <ButtonGris :showIcon="true" IconName="streamline:apple-solid" />
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
  </div>
  <div class="footerMovil">
    <div class="Endfooter">
      <div class="BttLinkSec">
        <div class="sec-text">For any questions, please contact steam@support.com</div>
      </div>
    </div>
    <div class="Frame61">
      <ButtonGris :showIcon="true" IconSize="1.5rem" IconName="streamline:computer-logo-facebook-2-media-facebook-social" />
      <ButtonGris :showIcon="true" IconSize="1.5rem" IconName="streamline:computer-logo-google-media-google-social" />
      <ButtonGris :showIcon="true" IconSize="1.5rem" IconName="streamline:adobe" />
      <ButtonGris :showIcon="true" IconSize="1.5rem" IconName="streamline:android" />
      <ButtonGris :showIcon="true" IconSize="1.5rem" IconName="streamline:apple-solid" />
    </div>
    <div class="Endfooter">
      <div class="Left">
        <div class="BttLinkSec">
          <div class="Link">@2024 Steam. All rights reserved</div>
        </div>
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
  width: 100%;
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

.Icons {
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

.footerMovil{
  display: none;
}

@media (max-width: 480px) {
  .Footer {
    display: none;
  }

  .footerMovil {
    width: 100%;
    height: 160px;
    padding: 25px;
    background: #151615;
    flex-direction: column;
    align-items: center;
    gap: 25px;
    display: inline-flex;
  }

  .Endfooter {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 182.14px;
    display: inline-flex;
  }

  .Frame61 {
    align-self: stretch;
    justify-content: center;
    align-items: center;
    gap: 8.24px;
    display: inline-flex;
  }

  .BttLinkSec {
    flex: 1 1 0;
    height: 14.30px;
    padding: 1.65px;
    justify-content: center;
    align-items: center;
    display: flex;
  }
  .Icons {
    width: 17.09px;
    height: 17.09px;
    position: relative;
  }

  .BoundingBox {
    width: 17.09px;
    height: 17.09px;
    left: 0px;
    top: 0px;
    position: absolute;
    background: #D9D9D9;
  }

  .Mail {
    width: 14px;
    height: 14px;
    left: 1.64px;
    top: 1.58px;
    position: absolute;
  }

  .Vector {
    width: 12.84px;
    height: 12.81px;
    left: 2.13px;
    top: 2.14px;
    position: absolute;
  }

  .Left {
    align-self: stretch;
    justify-content: space-between;
    align-items: flex-start;
    display: inline-flex;
  }

  .Link {
    color: var(--primary);
    font-size: 9.07px;
    font-family: Roboto;
    font-weight: 500;
    word-wrap: break-word;
  }

  .Link:last-child {
    color: #909090;
  }
}
</style>