<template>
  <header class="header flexRow ">
    <section class="logo ">
      <img src="/src/img/Logo.png">
    </section>
    <section class="flexRow" style="flex-grow: 1" @click="getScore()">
      <navigation :spaces="navs" @ChangePage="switchPage"></navigation>
    </section>
  </header>

  <!-- class="MainContent" -->
  <div v-if="currentPage == 'Inicio'" class="MainContent ">
    <home></home>
  </div>
  <div class="container tabla">
    <div v-if="currentPage == 'Ranking'" class="MainContent baseLine flexCenter">
      <ranking v-if="logged" :data="scores"></ranking>
      <a v-else @click="GoLogin" style="margin-top: 30%;"> Log in</a>
    </div>

    <div v-if="currentPage == 'Contacta Us'" class="MainContent flexCenter">
      <contact></contact>
    </div>

    <div v-if="currentPage == 'Mi perfil'" class=" MainContent flexCenter">

      <login v-if="!logged && !signin" :data="scores" @singin="changePage" @logIn="loggedIn"></login>
      <signIn v-if="!logged && signin" @singin="changePage" @signData="PostPlayer"></signIn>
      <insertData v-if="logged" @insert="PostScore" ></insertData>
    </div>
  </div>
  <gFotter></gFotter>

</template>

<script>
import navigation from "/src/components/Navigation.vue";
import ranking from "/src/components/Ranking.vue";
import contact from "/src/components/Contact.vue";
import gFotter from "/src/components/Footer.vue";
import login from "/src/components/LogIn.vue";
import home from "/src/components/HomePage.vue"
import signIn from "./components/SignIn.vue";
import insertData from "/src/components/InsertData.vue"
export default {
  components: {
    navigation,
    ranking,
    contact,
    gFotter,
    login, home,
    signIn,
    insertData
  },
  data() {
    return {
      navs: ["Inicio", "Ranking", "Contacta Us", "Mi perfil"],
      currentPage: 'Inicio',
      scores: Object,
      logged: false,
      signin: false,
      currentUser: []
    }

  },
  methods: {
    switchPage(content) {
      this.currentPage = content;
    },
    getScore() {
      fetch("https://localhost:7285/api/Entity")
        .then(res => {
          if (res.ok) {
            res.json().then((json) => {
              this.scores = json.data;
            })
          } else {
            throw new Error("")
          }
        })
        .catch((err => {
          console.log(err);
        }))
    },
    PostPlayer(data) {
      const url = 'https://localhost:7285/api/Entity/players';
      const playerData = {
        playerName: data[0],
        password: data[1],
        keysQuantity: 0,
        artifactsUnlocked: 0,
        scores: []
      };
      fetch(url, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(playerData)
      })
        .then(res => {
          if (res.ok) {
            this.signin = false;
            return res.json();
          } else {
           alert("Ya es existe el usuario")
          }
        })
        .catch(err => {
          console.log('Error creating player:', err);
        });
    }
    ,
    PostScore(score) {
      const url = 'https://localhost:7285/api/Entity/scores';
      const scoreData = {
        playerId: this.currentUser[0],
        value: score,
        player: {
          playerName: this.currentUser[1],
          password: "string"
        }
      };
      fetch(url, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(scoreData)
       
      } )
        .then(res => {
          if (res.ok) {
            
            return res.json();
          } else {
            throw new Error('Failed to create player');
          }
        })
        .catch(err => {
          console.log('Error creating player:', err);
        });
    }
    ,
    loggedIn(content) {

      this.currentUser = content
      this.logged = true;
    },
    GoLogin() {
      this.currentPage = "Mi perfil";
    },
    changePage(content) {

      this.signin = content;

    }
  }
}
</script>

<style>
.flexCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}

.baseLine {
  align-items: baseline;
}

.MainContent {
  height: 75vh;
}

.tabla {
  overflow-y: scroll;
}

.header {
  width: 100vw;
  height: auto;
}

.header>* {
  color: rgba(17, 151, 84, 0.443);
}

.contact {
  margin-top: 5vh;
}

.w50 {
  width: 50vw;
  min-width: 200px;
}


.flexRow {
  display: flex;
  flex-direction: row;
}

.centered {
  align-items: center;
}

.flexFill {
  flex: 1;
}

button {
  width: 100%;
  min-width: 40px;
  height: 100%;
  min-height: 30px;
  border: 0px;
  font-size: 16px;
  font-weight: 900;
  color: rgb(8, 111, 56);
  transition: background-color 0.5s ease, color 0.5s ease;

}

input {
  height: 30px;

}

input:focus {
  outline: none;
  box-shadow: none;
}

button:hover {
  color: white;
  background-color: rgba(17, 151, 84, 0.443);
}

.flexCol {
  display: flex;
  flex-direction: column;
}

.logo {
  display: grid;
  width: 150px;
  justify-content: center;

}

input:focus::placeholder {
  color: transparent;
}

/*  */
</style>