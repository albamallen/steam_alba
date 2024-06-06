<template>
    <div class="Property1Default">
        <div class="Searchbar">
            <div class="Textinputsec">
                <input type="text" v-model="searchQuery" class="SearchInput" placeholder="Search..."
                    @focus="isFocused = true" @blur="isFocused = false">
            </div>
            <ButtonGris :showIcon="true" IconName="line-md:search" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            searchQuery: '',
            isFocused: false
        };
    },
    methods: {
        search() {
            // Implementar la lógica de búsqueda
            console.log('Realizar búsqueda con:', this.searchQuery);
        }
    }
}
</script>

<style scoped>
.Property1Default {
    padding: 30px 0px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 30px;
}

.Searchbar {
    height: 80px;
    padding: 30px 10px 30px 20px;
    background: #D5D5D5;
    border-radius: 41px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
}

.Textinputsec {
    height: 49px;
    padding-top: 15px;
    padding-bottom: 15px;
    border-bottom: 1px black solid;
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
}

.SearchInput {
    width: 100%;
    height: 100%;
    border: none;
    outline: none;
    background: transparent;
    color: #6C6C6C;
    font-size: 16px;
    font-family: SF Mono;
    font-weight: 400;
}

@media (max-width: 480px) {
    .Property1Default {
        padding: 0;
    }
}
</style>