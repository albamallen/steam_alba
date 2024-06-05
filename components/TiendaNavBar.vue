<template>
    <div class="Righthero">
        <div class="Frame152">
            <NuxtLink to="/tienda" :class="{ 'active': currentPage === '/tienda' }" class="link">
                <h4>Nuevos y destacables</h4>
            </NuxtLink>
            <NuxtLink to="/tiendaJuegos" :class="{ 'active': currentPage === '/tiendaJuegos' }" class="link">
                <h4>Juegos por
                    tipo</h4>
            </NuxtLink>
            <NuxtLink to="/tiendaOfertas" :class="{ 'active': currentPage === '/tiendaOfertas' }" class="link">
                <h4>Ofertas</h4>
            </NuxtLink>
            <NuxtLink to="/tiendaPuntos" :class="{ 'active': currentPage === '/tiendaPuntos' }" class="link">
                <h4>Tienda de
                    puntos</h4>
            </NuxtLink>
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
    color: var(--100);
    text-decoration: none;
    transition: color 0.3s, background-color 0.3s;
    color: var(--100);
    background-color: var(--700);
    border-radius: 41px;
    padding: .25rem 1rem;
}

.link:hover {
    color: var(--700);
    background-color: var(--100);
    border-radius: 41px;
    padding: .25rem 1rem;
}

.active {
    background: var(--primary);
    border-radius: 41px;
    border: 1px var(--primary) solid;
    padding: .25rem 1rem;
}

@media (max-width: 480px) {
    .Frame152 {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        align-items: flex-start;
    }
}
</style>