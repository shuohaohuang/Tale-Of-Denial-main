<template>
    <section>
        <article>
            <img src="/src/img/user.png" class="imga">
            <input v-model="user" type="text" placeholder="nombre de usuario">
        </article>
        <article>
            <img src="/src/img/pass.png" class="imgb">
            <input v-model="password" type="password" placeholder="contraseña">
        </article>
        <article class="btts">
            <button class="lin" @click="verify">Registrarse</button>
        <button @click="singin">Iniciar sesion</button>
        </article>

    </section>
</template>

<script>
export default {
    props:{
        data: Array
    },
    data() {
        return {
            user: "",
            password: "",
            defaultValue: ["nombre de usuario",
                "contraseña"],
        }
    },
    methods: {
        verify() {
            console.log("me estoy registrando")
            this.$emit("signData",[this.user,this.password])
        },
        setblank(event) {
            if (this.defaultValue.some(event.target.value)) {
                console.log(this.defaultValue.includes(event.target.value))
                event.target.value = '';
            }
        },
        setDefaltPass(event) {
            if (event.target.value == "")
                event.target.value = this.defaultValue[1];
        },
        setDefaultUser(event) {
            if (event.target.value == "")
                event.target.value = this.defaultValue[0];
        },
        singin(){
            console.log("me voy a loguear")
            this.$emit("singin",false);
        }
    }
}
</script>

<style scoped>
* {
    background-color: white;
}

section {

    max-width: 500px;
    height: 60%;
    padding: 1vh;
    width: 70vw;
    display: flex;
    flex-direction: column;
    place-items: center;
    border: 3px rgba(17, 151, 84, 0.443) solid;
    gap: 10px;
}

article {
    display: flex;
    flex-direction: row;
    width: 80%;
    margin-top: 15%;
    height: 10%;
    border-bottom: rgba(17, 151, 84, 0.443) 2px solid;
    align-items: center;
    border-bottom: -5px;
}

.btts {
    flex-direction: column;
    width: 50%;
    align-items: center;
    height: auto;
    border-bottom: none;
}



input {
    background-color: rgb(100, 100, 100);
    color: white;
    flex-grow: 1;
}

::placeholder {
    color: white;
    opacity: 1;
}

.imga {
    width: 26px;
    height: 30px;
}

.imgb {
    width: 26px;
}
</style>