<template>
    <div class="Property1Default">
        <div class="Frame240">
            <div class="Frame245">
                <div class="BttDot"></div>
                <div class="Frame242">
                    <div class="Frame242">
                        <div :class="{ 'Subtitulo': true }">{{ HeadingText }}</div>
                    </div>
                </div>
            </div>
            <div v-if="showButton" class="BttIcons">
                <ButtonGris :showIcon="true" IconName="ic:baseline-keyboard-arrow-down" />
            </div>
            <div v-if="showPuntos" class="BttIcons">
                <ButtonGris :showText="true" buttonText="13,95€" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        buttonText: {
            type: String,
            default: "Default Text"
        },
        HeadingText: {
            type: String,
            default: "Heading 2"
        },
        showButton: {
            type: Boolean,
            default: true
        },
        showPuntos: {
            type: Boolean,
            default: true
        },
    }
};
</script>

<style scoped>
.Property1Default {
    width: 1728px;
    height: 120.59px;
    padding-top: 61px;
    padding-bottom: 20px;
    padding-left: 80px;
    padding-right: 80px;
    justify-content: flex-start;
    align-items: center;
    gap: 40px;
    display: inline-flex;
}

.Frame240 {
    justify-content: flex-start;
    align-items: center;
    gap: 40px;
    display: flex;
}

.Frame245 {
    align-self: stretch;
    justify-content: flex-start;
    align-items: center;
    gap: 15px;
    display: flex;
}

.BttDot {
    width: 19px;
    height: 19px;
    padding: 5.71px;
    background: #00FF03;
    border-radius: 24.54px;
}

.Frame242 {
    align-self: stretch;
    justify-content: flex-start;
    align-items: center;
    gap: 10px;
    display: flex;
}

.Subtitulo {
    color: #151615;
    font-size: 22px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
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

.ArrowBackIos {
    width: 14.12px;
    height: 14.12px;
    left: 3.10px;
    top: 14.05px;
    position: absolute;
    transform: rotate(-90deg);
    transform-origin: 0 0;
}

.ArrowBackIos .BoundingBox {
    width: 14.12px;
    height: 14.12px;
    left: 0px;
    top: 0px;
    position: absolute;
    transform: rotate(-90deg);
    transform-origin: 0 0;
    background: #D9D9D9;
}

.ArrowBackIos .ArrowBackIos {
    width: 6.52px;
    height: 11.74px;
    left: 1.18px;
    top: -0.43px;
    position: absolute;
    transform: rotate(-90deg);
    transform-origin: 0 0;
    background: #151615;
}
</style>