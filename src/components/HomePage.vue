<template>
    <section>
        <article class="a">
            <img src="/src/img/Titulo _Juego.png" class="Icon ">
            <p>“A Tale of Denial” és un emocionant joc d’exploració de mapes procedurals que combina elements de combats estratègics amb mecàniques clàssiques de RogueLike. En aquest joc, els jugadors prenen el paper d'un aficionat arqueòleg que decideix aventurar-se per tot el món per estudiar i recuperar artefactes de cultures perdudes.
</p>
        </article>
        <article class="b">
            <img src="/src/img/Calamar.png" class="Character">
        </article>
    </section>
</template>

<script>
export default {
    name: 'BackgroundSection'
};
</script>

<style scoped>
section {
    background-image: url('/src/img/VistaJuego.PNG');
    background-size: cover;
    /* Ensure the image covers the entire section */
    background-position: center;
    /* Center the image */
    background-repeat: no-repeat;
    /* Prevent the image from repeating */
    width: 100%;
    /* Ensure the section takes full width */
    height: 100%;
    /* Set the height to fill the viewport */

    display: flex;
    flex-direction: row;
}

.a {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 10%;
}

.b {
    display: flex;
    align-items: center;
    justify-content: center;
    
}

p {
    max-width: 300px;
    width: auto;
    margin-left: 5px;
}

.Icon {
    width: 140px;
    height: 90px;
    border-radius: 50%;
}

.Character {
    width: 60%;
    height: 50%;
}

article {
    width: 50%;
}
</style>