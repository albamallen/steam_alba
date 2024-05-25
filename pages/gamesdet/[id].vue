<template>
    <div>
        <div v-if="data">
            <div class="Frame189">
                <div class="Frame191">
                    <img :src="data.background_image" alt="Game Image" class="Image86"
                        :style="{ height: `${getDescriptionWidth() * 0.5}px` }" />
                    <div class="Textcontainer">
                        <div class="Frame188">
                            <div class="Textdiv">
                                <Genero />
                                <div class="NombreDelJuego">{{ data.name }}</div>
                                <div class="Description" v-html="data.description"></div>
                            </div>
                            <div class="Frame176">
                                <div class="Bttdiv align-end"> <!-- Aquí agregamos la clase align-end -->
                                    <Button buttonText="13,95€" />
                                </div>
                                <div class="BttIconLikeSmall">
                                    <ButtonGris :showIcon="true" IconName="line-md:plus" />
                                    <ButtonGris :showIcon="true" IconName="line-md:heart" />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-else-if="error">
            <p>Error fetching game data: {{ error.message }}</p>
        </div>
        <div v-else>
            <p>Loading...</p>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import { useRoute } from 'vue-router';
import Genero from '../components/Genero.vue';
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';

const route = useRoute();
const data = ref(null);
const error = ref(null);

const getDescriptionWidth = () => {
    if (!data.value) return 0;
    const description = data.value.description || '';
    return description.length;
};

const fetchGameData = async () => {
    const apiKey = '9a49841e50b64aeaafa0b18bee4b2e30';
    const gameId = route.params.id;

    try {
        const response = await axios.get(`https://api.rawg.io/api/games/${gameId}?key=${apiKey}`);
        data.value = response.data;
    } catch (err) {
        error.value = err;
        console.error('Error fetching game data:', err);
    }
};

onMounted(fetchGameData);
</script>


<style scoped>
.Frame189 {
    width: 100%;
    justify-content: flex-start;
    align-items: center;
    gap: 119px;
    display: inline-flex;
    margin-left: 4rem;
}

.Frame191 {
    justify-content: flex-start;
    gap: 119px;
    display: flex;
}

.Image86 {
    width: 750px;
    /* Se establece altura automática para adaptarse a la descripción */
    border-radius: 68px;
    object-fit: cover;
}

.Textcontainer {
    width: 700px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 71px;
    display: inline-flex;
}

.Frame188 {
    align-self: stretch;
    height: 446px;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 71px;
    display: flex;
}

.Textdiv {
    margin-top: 2rem;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    display: flex;
}

.BttLabel {
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 5px;
    padding-bottom: 5px;
    background: white;
    justify-content: flex-start;
    align-items: center;
    gap: 10px;
    display: inline-flex;
}

.Label {
    color: #151615;
    font-size: 16px;
    font-family: SF Mono;
    font-weight: 400;
    word-wrap: break-word;
}

.NombreDelJuego {
    color: #151615;
    font-size: 40px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
}

.Description {
    /* align-self: stretch; */
    color: #151615;
    font-size: 18px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
}

.Frame176 {
    justify-content: flex-start;
    align-items: center;
    display: inline-flex;
}

/* Estilos para la clase align-end */
.align-end {
    justify-content: flex-end;
}

.BttPrimary {
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    background: #00FF03;
    border-radius: 45px;
    justify-content: center;
    align-items: center;
    display: flex;
}

.Normal {
    color: #151615;
    font-size: 30px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
}

.BttIconLikeSmall {
    justify-content: center;
    align-items: center;
    display: flex;
}

.Icons {
    width: 20.74px;
    height: 20.74px;
    position: relative;
}

.BoundingBox {
    width: 20.74px;
    height: 20.74px;
    left: 0px;
    top: 0px;
    position: absolute;
    background: #D9D9D9;
}

.Favorite {
    width: 15.46px;
    height: 14.42px;
    left: 0.86px;
    top: 1.25px;
    position: absolute;
    background: #151615;
}
</style>