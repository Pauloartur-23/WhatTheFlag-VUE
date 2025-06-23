<script setup>
import { RouterLink } from 'vue-router';
import { useAcertosStore } from '@/stores/acertos';
const acertosStore = useAcertosStore();
</script>

<template>
  <div class="end-screen">
    <div class="container">
      <h1 class="title">🏁 The Fim</h1>
      <h2 class="subtitle">Parabéns!!! 🎉</h2>
      <p class="score">Você conseguiu <strong>{{ acertosStore.acertos }}</strong> acertos!</p>
      <RouterLink to="/" class="link-button">
        <button>🔁 REINICIAR</button>
      </RouterLink>
    </div>
  </div>
</template>

<style scoped>
.end-screen {
  height: 100vh;
  background: linear-gradient(135deg, #f263ff, #781db4);
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  padding: 1rem;
  box-sizing: border-box;
}

.container {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  padding: 3rem;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.25);
  max-width: 500px;
  width: 100%;
}

.title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.subtitle {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.score {
  font-size: 1.5rem;
  margin-bottom: 2rem;
}

button {
  background-color: #ffffff;
  color: #f263ff;
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
