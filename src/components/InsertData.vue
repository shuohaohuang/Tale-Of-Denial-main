<template>
    <section>
        <article>
            <p>Score</p>
        </article>
        <article>
            <input type="number" v-model="score">
        </article>
        <button @click="insert">Insertar</button>
    </section>

</template>

<script>
export default {
    data() {
        return {
            score: 0
        }
    },
    methods: {
        insert() {
            this.$emit("insert", this.score);
        }
    }
}
</script>

<style>
input {
    color: black;
}
</style>