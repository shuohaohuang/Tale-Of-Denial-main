<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section>
        <article>
            <label class>Nombre</label>
            <input type="text">
        </article>

        <article>
            <label>Correo</label>
            <input type="text">
        </article>

        <article>
            <label>Direccion</label>
            <input type="text">
        </article>
        <article class="btt">
            <button>Enviar</button>
        </article>


    </section>


</template>


<style scoped>
* {
    background-color: white;
}

section {
    max-width: 500px;
    height: auto;
    padding: 1vh;
    width: 70vw;
    display: flex;
    flex-direction: column;
    place-items: center;
    border: 3px rgba(17, 151, 84, 0.443) solid;
    gap: 10px;
}

article {
    display: grid;
    width: 80%;
}

.btt {
    margin-top: 10px;
    margin-bottom: 20px;
}

label {
    color: rgb(53, 53, 53);
}

input {
    background-color: rgb(100, 100, 100);
    color: white;
}
</style>