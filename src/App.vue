<template>
  <div id="app">
    <img class="background-image" src="./assets/Vector.svg" alt="background image">
    <header class="header">
      <div><img src="./assets/union.png" alt="logo union" /></div>
      <div>
        <p>
          github
          <span>_explorer</span>
        </p>
      </div>
    </header>
    <div class="explore">
      <h1>Explore repositórios no Github.</h1>
      <div>
        <input v-model="searchUser" type="text" placeholder="Digite aqui" />
        <button @click="getRepositoriesByUsername()">Pesquisar</button>
      </div>
    </div>
    <div class="cards">
      <div class="card">
        <Cards v-for="card in responseData" :repositories="card" />
      </div>
    </div>
  </div>
</template>

<script>
import Cards from "./components/Cards.vue";
import api from "./services/api";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Cards,
  },
  data() {
    return {
      // items: [
      //   { message: "João" },
      //   { message: "Gab" },
      //   { message: "Kamily" },
      //   { message: "Victor" },
      // ],
      searchUser: '',
      responseData: {},
    };
  },
  methods: {
    getRepositoriesByUsername() {
      console.log(this.searchUser);
      axios.get(`https://api.github.com/users/${this.searchUser}/repos`)
      .then(response => {
        this.responseData = response.data;
      }).catch(function(error) {
        console.log("ocorreu um erro "+error);
      });
    },
  }
};
</script>

<style lang="scss">
$font-title: normal 700 36px "Arial";

body {
  margin: 0;
  background-color: #e5e5e5;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 0 36px;
  margin: 0 auto;
  max-width: 960px;
}

.background-image {
  position: absolute;
  opacity: 0.2;
  z-index: -1;
}

.header {
  display: flex;
  align-items: center;
  gap: 12px;
  padding-top: 18px;
  img {
    width: 18px;
    height: 18px;
  }
  p {
    font: normal 700 12px "Arial";
    color: #737380;
    span {
      color: #a8a8b3;
    }
  }
}

.explore {
  h1 {
    font: $font-title;
    text-align: left;
  }
  div {
    display: flex;
  }
  input {
    width: 100%;
    height: 54px;
    box-sizing: border-box;
    padding: 0;
    border: none;
    border-radius: 5px 0px 0px 5px;
    padding-left: 30px;
    font: normal 400 12px "Arial";
    color: #a8a8b3;
  }
  button {
    grid-column: 5/6;
    background-color: #04d361;
    width: 90px;
    height: 54px;
    border: none;
    border-radius: 0px 5px 5px 0px;
    font: normal 700 12px "Arial";
    color: #fff;
  }
}
</style>
