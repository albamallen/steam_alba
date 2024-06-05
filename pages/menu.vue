<template>
    <div>
        <div class="menu">
            <ButtonGris :showIcon="true" IconName="line-md:search" />
            <div class="right-nav">
                <div class="button-container">
                    <NuxtLink to="/tienda"
                        :class="{ 'nav-link h4': $route.path !== '/pagina1', 'nav-link-bold': $route.path === '/pagina1' }">
                        <h4>Tienda</h4>
                    </NuxtLink>
                </div>
                <div class="button-container">
                    <NuxtLink to="/soporte"
                        :class="{ 'nav-link h4': $route.path !== '/pagina1', 'nav-link-bold': $route.path === '/pagina1' }">
                        <h4>Soporte</h4>
                    </NuxtLink>
                </div>
            </div>
            <nuxt-link to="/">
                <ButtonGris :showIcon="true" IconName="line-md:close-small" />
            </nuxt-link>
        </div>
    </div>
</template>

<style>
@media (max-width: 480px) {
    .menu {
        background: linear-gradient(180deg, #ffffff 0%, #00FF03 110%);
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100vh;
        width: 100%;
        gap: 2rem;
        padding-top: 5rem;
    }
}
</style>