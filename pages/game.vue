<template>
    <div class="big_card_game">
        <img style="width: 750px; height: 580px; border-radius: 68px" src="https://via.placeholder.com/750x580" />
        <div class="card_right w-96 h-80 flex-col justify-between items-start inline-flex">
            <div class="px-2.5 py-1 bg-white justify-start items-center gap-2.5 inline-flex">
                <div class="genre text-neutral-900 text-base font-normal">Género</div>
            </div>
            <div class="w-80 text-neutral-900 text-4xl font-medium">Nombre del juego
            </div>
            <div class="self-stretch text-neutral-900 text-lg font-medium">Establece y
                expande tus propios asentamientos, libera la tierra y ayuda a sus aldeanos. Recluta a otros para tu
                causa
                mientras aprendes más sobre la vida que tuviste que dejar atrás. Dirige a tus fuerzas, demuestra tu
                valor en
                el combate y consolida tu lugar como el héroe de tu pueblo.</div>
            <div class="card_right_below">
                <div class="price_button">
                    <p class="price text-xl">13,95€</p>
                </div>
                <div class="heart_icon">
                    <Icon name="line-md:heart" size="2em" color="black"></Icon>
                </div>
            </div>
        </div>


    </div>
</template>

<style scoped>
.big_card_game {
    display: flex;
    flex-direction: row;
    padding: 4rem;

    .card_right {
        margin: 3.5rem;
        font-family: Roboto;
        .genre {
            font-family: DM Mono;
        }

        .card_right_below {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            gap: 1rem;
            margin-top: 2rem;
            .price_button{
                align-items: center;
                background-color: var(--primary);
                padding:.8rem;
                font-weight: bold;
                border-radius: 50px;
            }
        }
    }
}
</style>