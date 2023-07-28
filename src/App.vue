<script setup>
import { ref } from 'vue';
import Card from './components/Card.vue';

// Variable for API
let favoritos = ref('');
let users = ref([]);
let loading = ref(true);

// Usuario favorito
const añadirFavorito = (cardFavorito) => {
 favoritos.value = cardFavorito;};

// API
const getData = async () => {
  try {
    const res = await fetch('https://raw.githubusercontent.com/a01659224B/QuizPWBibiana/main/APIUSER.js');
    users.value = await res.json();
  } catch (error) {
    console.log(error);
  } finally {
    setTimeout(() => {
      loading.value = false;
    }, 1000);
  }
};

getData();
</script>

<template>
  <div class="app">
    <h1>User favorito:  {{ favoritos }}</h1>
    <div class="user-list">
      <section>
        <Card v-for="item in users" :key="item.id"
          :nombre="item.nombre"
          :id="item.id"
          :edad="item.edad"
          :email="item.email"
          @añadirFavorito="añadirFavorito(item.nombre)"
        />
      </section>
    </div>
  </div>
</template>

<style>
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

.user-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
}
</style>
