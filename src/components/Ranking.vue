<!-- eslint-disable vue/require-v-for-key -->
<template>
    <div>
        <section>
            <article class="table flexRow spcarn">
                <p class="break-word">Player</p>
                <p class="break-word">Puntuación maxima</p>
                <p class="break-word"> Llaves</p>
                <p class="break-word">Artefactos desbloqueados</p>
            </article>
            <article v-for="user in data" class="table" id="content">

                <p class="break-word">{{ user.playerName }}</p>
                <p class="break-word">{{ getMax(user) }}</p>
                <p class="break-word">{{ user.keysQuantity==null? 0: user.keysQuantity}}</p>
                <p class="break-word">{{ user.artifactsUnlocked ==null? 0: user.artifactsUnlocked}}</p>
            </article>
        </section>

    </div>
</template>

<script>
export default {
    name: "Ranking-Table",
    props: {
        data: Array
    },
    methods: {
        getMax(user) {
            console.log(user.scores.length== 0)
            if (user.scores.length == 0)
                return 0;

            return user.scores.reduce((max, current) => {
                const value = current.value === undefined ? 0 : current.value;
                return value > max ? value : max;
            }, 0)
        }
    }
}</script>

<style scoped>
.spcarn {
    justify-content: space-around;
}

section {
    width: 90%;
}

article {
    width: 100%;
}

img {
    width: 90%;
    max-width: 100px;
}

p {
    min-width: 50px;
    width: 25%;
    font-size: 1em;
    text-align: center;

    word-break: break-all;
}

.table {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-left: 5px;
    margin-right: 5px;
    margin-bottom: 1px;
    margin-top: 10px
}
</style>
