<template>
    
    <div class="herocard">
        <div class="img-container">
            <img :src="highlightGame.background_image" alt="Game Image" class="game-image" />
        </div>
        <div class="heromodal">
            <div class="juego-destacado">{{ highlightGame.name }}</div>
            <div class="text">
                <p>{{ truncatedDescription }}</p>
            </div>
            <div class="bttdiv">
                <div class="btt-primary">
                    <Button buttonText="50,99" />
                </div>
                <div class="btt-icon-like">
                    <div class="icons">
                        <ButtonGris :showIcon="true" IconName="line-md:heart" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        highlightGame: {
            type: Object,
            required: true
        }
    },
    computed: {
        truncatedDescription() {
            if (!this.highlightGame.description) {
                return 'No description available';
            }
            const lines = this.highlightGame.description.split('\n');
            const maxLines = 10;
            if (lines.length > maxLines) {
                return lines.slice(0, maxLines).join('\n') + '...';
            }
            return this.highlightGame.description;
        }
    }
};
</script>

<style scoped>
.herocard {
    width: 100%;
    max-width: 340px;
    height: 573px;
    background: white;
    border-radius: 32px;
    overflow: hidden;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.img-container {
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 18px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
}

.game-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 18px;
}

.heromodal {
    position: absolute;
    padding: 25px 50px;
    background: rgba(21, 22, 21, 0.7);
    border-radius: 29px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 35px;
    bottom: 20px;
}

.juego-destacado {
    color: #fdfdfd;
    font-size: 30px;
    font-family: 'Neue Haas Grotesk Text Pro', sans-serif;
    font-weight: 500;
    text-align: center;
}

.text {
    color: white;
    opacity: 0.8;
    font-size: 14px;
    text-align: center;
    max-height: 13.19em;
    /* Approx. height of 10 lines */
    overflow: hidden;
    position: relative;
}

.text p {
    display: -webkit-box;
    -webkit-line-clamp: 10;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
}

.bttdiv {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
}

.btt-primary {
    border-radius: 32px;
    padding: 10px 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.btt-icon-like {
    border-radius: 50%;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>