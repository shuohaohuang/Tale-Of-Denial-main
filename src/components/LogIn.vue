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
            <button class="lin" @click="verify">Iniciar sesion</button>
            <button class="sin" @click="singin">Regitrarse</button>
        </article>

    </section>
</template>

<script>
export default {
    props: {
        data: Array

    },
    data() {
        return {
            user: "",
            password: "",
            userData: [],
            defaultValue: ["nombre de usuario",
                "contraseña"],
        }
    },
    methods: {
        verify() {
            if (this.data.some(user => user.playerName == this.user && user.password == this.password)) {
                const matchedUser = this.data.find(user => user.playerName === this.user && user.password === this.password);
                if (matchedUser) {
                    this.userData = [
                        matchedUser.id
                        , matchedUser.playerName
                    ];
                    this.Logged();
                }
            }
            else
                alert("Usuario o contraseña incorrectos")
        },
        Logged() {
            this.$emit("logIn", this.userData)
        },
        setblank(event) {
            if (this.defaultValue.some(event.target.value)) {
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
        singin() {
            this.$emit("singin", true);
        }
    }
}
</script>

<style scoped>
* {
    background-color: white;
}

.sin>p {
    border-bottom: 3px rgba(17, 151, 84, 0.443) solid;
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