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
                                <div class="btt-genero" v-if="data.genres && data.genres.length">
                                    <div class="genero sec-p">{{ data.genres[0].name }}</div>
                                </div>
                                <div class="NombreDelJuego">{{ data.name }}</div>
                                <div class="Description" v-html="data.description"></div>
                            </div>
                            <div class="Frame176">
                                <div class="Bttdiv align-end">
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
        <HeaderSubtitulo HeadingText="Opiniones" :showPagar="false" :showButton="false" :showPuntos="false" />

        <div class="opiniones">
            <OpinionCard v-for="(user, index) in displayedUsers" :key="index" :user="user" class="opinion-card" />
        </div>
        <div v-if="users.length > displayedUsers.length" class="load-more">
            <button @click="loadMoreUsers">Load more</button>
        </div>
        <HeaderSubtitulo HeadingText="Juegos Relacionados" :showPagar="false" :showButton="false" :showPuntos="false" />

    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import { useRoute } from 'vue-router';
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';
import OpinionCard from '../components/OpinionCard.vue';

const route = useRoute();
const data = ref(null);
const error = ref(null);
const users = ref([]);
const displayedUsers = ref([]);
const usersToShow = 3;

const getDescriptionWidth = () => {
    if (!data.value) return 0;
    const description = data.value.description || '';
    return description.length;
};

const fetchGameData = async () => {
    const apiKey = '6ef278bbca324856844d239c28a65278';
    const gameId = route.params.id;

    try {
        const response = await axios.get(`https://api.rawg.io/api/games/${gameId}?key=${apiKey}`);
        data.value = response.data;
    } catch (err) {
        error.value = err;
        console.error('Error fetching game data:', err);
    }
};

const fetchUserData = async () => {
    try {
        const response = await axios.get('https://fakestoreapi.com/users');
        users.value = response.data.map(userData => ({
            name: `${userData.name.firstname} ${userData.name.lastname}`,
            email: userData.email,
            picture: `https://via.placeholder.com/81x81?text=${userData.username}`
        }));
        displayedUsers.value = users.value.slice(0, usersToShow);
    } catch (err) {
        console.error('Error fetching user data:', err);
    }
};

const loadMoreUsers = () => {
    const nextIndex = displayedUsers.value.length;
    displayedUsers.value = users.value.slice(0, nextIndex + usersToShow);
};

onMounted(() => {
    fetchGameData();
    fetchUserData();
});
</script>

<style scoped>
.Frame189 {
    width: 100%;
    justify-content: flex-start;
    align-items: center;
    gap: 119px;
    display: inline-flex;
    padding-left: 4rem;
}

.Frame191 {
    justify-content: flex-start;
    gap: 119px;
    display: flex;
}

.Image86 {
    width: 750px;
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

.align-end {
    justify-content: flex-end;
}

.BttIconLikeSmall {
    justify-content: center;
    align-items: center;
    display: flex;
    gap: 2rem;
}

.genero {
    color: var(--100);
    word-wrap: break-word;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    max-width: 100%;
}

.btt-genero {
    padding: 5px 10px;
    background: var(--700);
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 10px;
}

.opiniones {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 2rem;
    padding-top: 2rem;
}

.opinion-card {
    box-sizing: border-box;
}

.load-more {
    text-align: center;
    margin-top: 2rem;
}
</style>