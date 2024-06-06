<template>
    <div class="Frame195">
        <div class="Frame182">
            <div class="Frame179">
                <div class="Img" :style="{ backgroundImage: `url(${user.picture})` }">
                    <img class="Image59" :src="user.picture" />
                </div>
                <div class="Frame178">
                    <h4 class="username">{{ user.name }}</h4>
                    <h5 class="email">{{ user.email }}</h5>
                </div>
            </div>
            <h5 class="ReviewText">
                {{ userReview }}
            </h5>
            <div class="Frame181">
                <div class="Frame180">
                    <div class="Rating">4.5</div>
                    <div class="KidStar">
                        <Icon name="line-md:star" size="2em"></Icon>
                    </div>
                </div>
                <div class="BttIcons">
                    <div class="Icons">
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
        user: {
            type: Object,
            required: true
        },
        userReview: {
            type: String,
            default: 'Establece y expande tus propios asentamientos, libera la tierra y ayuda a sus aldeanos. Recluta a otros para tu causa mientras aprendes más sobre la vida que tuviste que dejar atrás. Dirige a tus fuerzas, demuestra tu valor en el combate y consolida tu lugar como el héroe de tu pueblo.'
        }
    }
};
</script>

<style scoped>
.Frame195 {
    padding: 45px 33px;
    background: #151615;
    border-radius: 30px;
    overflow: hidden;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
    display: inline-flex;
}

.Frame182 {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 51px;
    display: inline-flex;
}

.Frame179 {
    justify-content: flex-start;
    align-items: center;
    gap: 29px;
    display: inline-flex;
}

.Img {
    width: 81px;
    height: 81px;
    border-radius: 103px;
    overflow: hidden;
    background-size: cover;
    background-position: center;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: inline-flex;
}

.Frame178 {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 8px;
    display: inline-flex;
}

.username {
    color: white;
    word-wrap: break-word;
}

.email {
    color: white;
    word-wrap: break-word;
}

.ReviewText {
    width: 100%;
    color: #FDFDFD;
    word-wrap: break-word;
}

.Frame181 {
    justify-content: flex-start;
    align-items: center;
    gap: 131px;
    display: inline-flex;
}

.Frame180 {
    justify-content: flex-start;
    align-items: center;
    gap: 16px;
    display: flex;
}

.Rating {
    color: #28EB32;
    font-size: 40px;
    font-family: DM mono, monospace;
    font-weight: 400;
    word-wrap: break-word;
}

.KidStar {
    width: 32.86px;
    height: 35.17px;
    color: #00FF03;
}

.BttIcons {
    padding: 2.92px 5.84px;
    border-radius: 40.71px;
    justify-content: center;
    align-items: center;
    display: flex;
}

.Icons {
    width: 47.32px;
    height: 53.16px;
    position: relative;
}

.BoundingBox {
    width: 47.32px;
    height: 53.16px;
    left: 0;
    top: 0;
    position: absolute;
}

@media (max-width: 480px) {
    .Frame181 {
        display: none;
    }

    .Frame182 {
        flex-direction: column;
        justify-content: flex-start;
        align-items: flex-start;
        gap: 20px;
        display: inline-flex;
    }

    .Frame195 {
        width: 100px;
        padding: 1rem;
        background: #151615;
        border-radius: 30px;
        overflow: hidden;
        justify-content: flex-start;
        align-items: flex-start;
        gap: 10px;
        display: inline-flex;
    }

    .ReviewText {
        width: 50%;
        color: #FDFDFD;
        word-wrap: break-word;
        display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
    }


}
</style>