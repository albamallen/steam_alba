<template>
    <div>
        <HeaderTitulo title="Tienda" />
        <TiendaNavBar />
        <HeaderSubtitulo HeadingText="Géneros" :showPuntos="false"/>
        <div class="generos"><CardTipo botonTexto="Rol" /><CardTipo botonTexto="Estrategia" /><CardTipo botonTexto="Storytelling" /><CardTipo botonTexto="Indie" /><CardTipo botonTexto="Aventuras" /><CardTipo botonTexto="Arcade" /></div>
        <HeaderSubtitulo HeadingText="Tipos de juego" :showPuntos="false"/>
        <div class="generos"><CardTipo botonTexto="Individual" /><CardTipo botonTexto="Multijugador" /><CardTipo botonTexto="Online" /></div>
    </div>
</template>


<style>

.generos{
    background-color: var(--100);
    padding: 2rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}

</style>