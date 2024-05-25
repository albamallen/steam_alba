<template>
    <div>
        <HeaderTitulo title="Tienda" />
        <TiendaNavBar />
        <HeaderSubtitulo headingText="Tus puntos" :showButton="false" :showPuntos="true"/>
        <div class="cards"><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /></div>
        
    </div>
</template>