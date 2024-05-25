<template>
    <div class="Righthero">
        <div class="Frame152">
            <NuxtLink to="/tienda" :class="{ 'active': currentPage === '/tienda' }" class="link">Nuevos y destacables
            </NuxtLink>
            <NuxtLink to="/tiendaJuegos" :class="{ 'active': currentPage === '/tiendaJuegos' }" class="link">Juegos por
                tipo</NuxtLink>
            <NuxtLink to="/tiendaOfertas" :class="{ 'active': currentPage === '/tiendaOfertas' }" class="link">Ofertas
            </NuxtLink>
            <NuxtLink to="/tiendaPuntos" :class="{ 'active': currentPage === '/tiendaPuntos' }" class="link">Tienda de
                puntos</NuxtLink>
        </div>
    </div>
</template>

<script>
import ButtonGris from '../components/ButtonGris.vue';

export default {
    components: {
        ButtonGris
    },
    data() {
        return {
            currentPage: ''
        };
    },
    mounted() {
        this.currentPage = this.$route.path;
    }
};
</script>

<style scoped>
.Righthero {
    width: 100%;
    padding: 42px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
}

.Frame152 {
    justify-content: flex-start;
    align-items: center;
    gap: 45px;
    display: inline-flex;
}

.link {
    color: #151615;
    text-decoration: none;
    transition: color 0.3s, background-color 0.3s;
    color: #000;
    background-color: #ffff;
    border-radius: 41px;
    padding: .25rem 1rem;
}

.link:hover {
    color: #ffffff;
    background-color: #000000;
    border-radius: 41px;
    padding: .25rem 1rem;
}

.active {
    background: #00FF03;
    border-radius: 41px;
    border: 1px #00FF03 solid;
    padding: .25rem 1rem;
}
</style>