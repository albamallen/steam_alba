<template>
    <div class="Property1Default">
        <div class="Searchbar">
            <div class="Textinputsec">
                <input type="text" v-model="searchQuery" class="SearchInput" placeholder="Search..."
                    @focus="isFocused = true" @blur="isFocused = false">
            </div>
            <div class="BttIconSearch" :class="{ 'Active': isFocused }" @click="search">
                <div class="Icons">
                    <div class="Search">
                        <Icon name="line-md:search" size="2em"></Icon>
                    </div>
                </div>
            </div>
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
    padding: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 30px;
}

.Searchbar {
    height: 80px;
    padding: 30px;
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

.BttIconSearch {
    width: 62px;
    height: 62px;
    padding: 10px 20px;
    background: #D5D5D5;
    border-radius: 41px;
    justify-content: center;
    align-items: center;
    display: flex;
    cursor: pointer;
}

.BttIconSearch.Active {
    background: #B8B8B8;
}

.Icons {
    width: 51.90px;
    height: 51.90px;
    position: relative;
}

.BoundingBox {
    width: 100%;
    height: 100%;
    position: absolute;
    background: #D9D9D9;
}

.Search {
    width: 41.70px;
    height: 41.64px;
    left: 5.10px;
    top: 5.13px;
    position: absolute;
}
</style>