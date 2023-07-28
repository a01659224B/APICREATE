<script setup>
defineProps({
    nombre: String,
    id: Number,
    edad: Number,
    email: String,
});
const emit=defineEmits(['añadirFavorito'])
</script>

<template>
    <div class="card">
    <div>
      <h2>{{ id }} - {{ nombre }}</h2>
      <h5>{{ edad }} años</h5>
      <p>{{ email }}</p>
    </div>
    <div>
      <button @click="$emit('añadirFavorito', nombre)">Favorito</button>
    </div>
  </div>
  </template>
  
  <style>
  .card {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    margin: 10px;
    width: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  h2 {
    font-size: 18px;
    margin-bottom: 5px;
  }
  
  h5 {
    font-size: 14px;
    color: #555;
    margin-bottom: 10px;
  }
  
  p {
    font-size: 14px;
    color: #888;
    margin-bottom: 15px;
  }
  
  button {
    padding: 5px 10px;
    border: none;
    background-color: #007bff;
    color: #fff;
    border-radius: 3px;
    cursor: pointer;
    font-size: 14px;
  }
  
  </style>