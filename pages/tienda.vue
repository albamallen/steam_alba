<template>
    <div>
      <HeaderTitulo title="Tienda" />
      <TiendaNavBar />
      <div class="cards"><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /></div>

    </div>
</template>


<script>
import SingleCardGame from '~/components/SingleCardGame.vue';


export default {
  components: {
    
    SingleCardGame
  }
};
</script>


<style>
.cards{
  margin-left: 80px;
  margin-right: 20px; /* Margen derecho añadido */
  gap: 40px;
  display: flex;
  justify-content: flex-start;
  overflow-x: auto;
  width: calc(100% - 100px); /* Se ajusta el ancho teniendo en cuenta el margen izquierdo y derecho */
  white-space: nowrap;
}
</style>
