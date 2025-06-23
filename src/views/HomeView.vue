<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <div class="container">
    <h1 class="titulo">🌍 WhatTheFlag</h1>
    <div class="card">
      <h2>Como jogar?</h2>
      <p>🧠 O jogo tem 3 fases.</p>
      <p>📚 Cada fase avalia um tipo de informação.</p>
      <p>⏱️ Você terá <strong>30 segundos</strong> para passar pelas fases.</p>
      <p>🏁 Escolha as bandeiras corretas com base no critério dado.</p>

      <RouterLink class="start-button" to="/game">
        <button>INICIAR</button>
      </RouterLink>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: linear-gradient(135deg, #f263ff, #781db4);
  color: #fff;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.titulo {
  font-size: 3rem;
  margin-bottom: 20px;
}

.card {
  background-color: rgba(255, 255, 255, 0.15);
  padding: 30px 40px;
  border-radius: 20px;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
  max-width: 400px;
  text-align: center;
}

.card h2 {
  margin-bottom: 15px;
  font-size: 1.5rem;
}

.card p {
  margin: 10px 0;
  font-size: 1rem;
  line-height: 1.4;
}

button {
  background-color: #ffffff;
  color: #d063ff;
  border: none;
  padding: 0.8rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #e0dbff;
  transform: scale(1.05);
}

.link-button {
  text-decoration: none;
}
</style>
