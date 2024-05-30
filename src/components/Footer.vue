<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <footer class="footer">
        <div class="footer-container">
            <div class="footer-section social">
                <h3>Redes Sociales</h3>
                <a href="https://es-es.facebook.com/enespanol/">
                    <img src="/src/img/facebook_logo_icon_189224.png" alt="">
                </a>
                <a href="https://x.com/">
                    <img src="/src/img/twitter_x_new_logo_x_rounded_icon_256078.png" alt="">
                </a>
                <a href="https://www.instagram.com/">
                    <img src="/src/img/Instagram_logo_2022.svg.webp" alt="">
                </a>
                <a href="https://www.youtube.com/">
                    <img src="/src/img/youtube_logo_icon_168737.png">
                </a>
            </div>
        </div>
        <div class="footer-container">
            <p>&copy; 2024 A Tale of Denial. Todos los derechos reservados.</p>
        </div>
    </footer>
</template>


<style scoped>
.footer {
    background-color: rgb(53, 53, 53);
    color: #ffffff;
    padding: 15px 0;
    text-align: center;
    border-top: rgba(17, 151, 84, 0.443) 2px solid;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}

.footer-container {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    max-width: 1200px;
    margin: auto;
    padding: 0 20px;
    
    
}
.footer-section {
    flex: 1;
    display: flex;
    min-width: 250px;
    margin: 20px 0;
    flex-direction: row;
}

h3{
   align-content: center;
   margin-right: 1%;
}

.footer-section ul {
    list-style: none;
    padding: 0;
}

.footer-section ul li {
    margin-bottom: 10px;
}

.footer-section ul li a {
    color: #ffffff;
    text-decoration: none;
}

.footer-section ul li a:hover {
    text-decoration: underline;
}

.footer-section .social a {
    margin: 0 10px;
    display: inline-block;
    color: #ffffff;
    font-size: 20px;
    text-decoration: none;
}

.footer-section .social a:hover {
    color: #3498db;
}

.footer-bottom {
    margin-top: 40px;
    font-size: 14px;
}

.footer-bottom p {
    margin: 0;
}

a {
    height: auto;
}

img {
    width: 45px;
    height: 45px;
}
</style>