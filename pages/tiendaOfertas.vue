<template>
    <div>
        <HeaderTitulo title="Tienda" />
        <TiendaNavBar />
        <HeaderSubtitulo HeadingText="Juegos gratuitos" :showButton="false" :showPuntos="false"/>
        <SwiperComponent />
        <div class="cards"><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /></div>
        <HeaderSubtitulo headingText="Promociones" :showButton="false" :showPuntos="false"/>
        <SwiperComponent />
        <div class="cards"><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /><SingleCardGame /></div>
    </div>
</template>