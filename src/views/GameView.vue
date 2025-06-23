<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { useRouter } from 'vue-router';
import { useAcertosStore } from '@/stores/acertos';

const router = useRouter();
const acertosStore = useAcertosStore();

import bandeiraChile from '/public/001-chile.png';
import bandeiraIreland from '/public/002-ireland.png';
import bandeiraGreece from '/public/003-greece.png';
import BandeiraNorway from '/public/004-norway.png';
import bandeiraIsrael from '/public/005-israel.png';
import bandeiraGuatemala from '/public/006-guatemala.png';
import bandeiraCuba from '/public/007-cuba.png';
import bandeiraCroatia from '/public/008-croatia.png';
import bandeiraPanama from '/public/009-panama.png';

const Bandeiras = [
  { nome: 'Chile', imagem: bandeiraChile, id: 1 },
  { nome: 'Ireland', imagem: bandeiraIreland, id: 2 },
  { nome: 'Greece', imagem: bandeiraGreece, id: 3 },
  { nome: 'Norway', imagem: BandeiraNorway, id: 4 },
  { nome: 'Israel', imagem: bandeiraIsrael, id: 5 },
  { nome: 'Guatemala', imagem: bandeiraGuatemala, id: 6 },
  { nome: 'Cuba', imagem: bandeiraCuba, id: 7 },
  { nome: 'Croatia', imagem: bandeiraCroatia, id: 8 },
  { nome: 'Panama', imagem: bandeiraPanama, id: 9 }
];

const timer = ref(30);
const borderStyles = ref({});
const clicadas = ref(new Set());
let intervalo = null;
const erros = ref(0);

function iniciarContagem() {
  intervalo = setInterval(() => {
    if (timer.value > 0) {
      timer.value--;
    } else {
      clearInterval(intervalo);
      router.push('/finish');
    }
  }, 1000);
}

function certo(id) {
  if (clicadas.value.has(id)) return;
  clicadas.value.add(id);

  const corretas = [1, 6, 7];

  if (corretas.includes(id)) {
    borderStyles.value[id] = '3px solid #00e676'; 
    acertosStore.acertos++;
    if (acertosStore.acertos === 3) {
      clearInterval(intervalo);
      router.push('/finish');
    }
  } else {
    borderStyles.value[id] = '3px solid #ff1744'; 
    erros.value++;
    if (erros.value >= 3) {
      clearInterval(intervalo);
      router.push('/finish');
    }
  }
}

onMounted(() => {
  acertosStore.acertos = 0;
  iniciarContagem();
});

onUnmounted(() => {
  clearInterval(intervalo);
});
</script>

<template>
  <div class="game-view">
    <div class="conteiner">
      <header>
        <h2>⏰ 00 : {{ timer < 10 ? '0' + timer : timer }}</h2>
        <h1>O idioma é espanhol?</h1>
        <p>Acertos {{ acertosStore.acertos }} / 3</p>
      </header>

      <ul class="flags-list">
        <li
          v-for="bandeira in Bandeiras"
          :key="bandeira.id"
          @click="certo(bandeira.id)"
          :style="{ border: borderStyles[bandeira.id] || '3px solid transparent' }"
        >
          <img :src="bandeira.imagem" :alt="bandeira.nome" />
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.game-view {
  height: 100vh;
  display: flex;
  justify-content: center; 
  align-items: center;     
  background: linear-gradient(135deg, #f263ff, #781db4);  
  padding: 1rem;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: white;
}

.conteiner {
  background: rgba(255 255 255 / 0.15);
  border-radius: 20px;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.25);
  max-width: 650px;
  width: 100%;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 80vh;
  box-sizing: border-box;
  padding: 2rem 4rem 2rem 2rem;
}

header h1 {
  font-size: 2.5rem;
  font-weight: 700;
  letter-spacing: 1px;
  margin-top: 0.25rem;
  margin-bottom: 0.5rem;
  margin-left: 2rem;
}

header h2 {
  font-size: 3rem;
  margin: 0;
  font-weight: 900;
  margin-left: 2rem;
}

header p {
  font-size: 1.5rem;
  margin-top: 0.5rem;
  font-weight: 600;
  margin-left: 2rem;
}

.flags-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
  margin-top: 2rem;
}

.flags-list li {
  list-style: none;
  border-radius: 15px;
  cursor: pointer;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.25);
  transition: transform 0.3s ease, border-color 0.3s ease;
  border: 3px solid transparent;
  background: rgba(255 255 255 / 0.1);
  width: 120px;
  height: 120px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.flags-list li:hover {
  transform: scale(1.05);
  border-color: #fff;
}

.flags-list img {
  max-width: 90px;
  max-height: 90px;
  border-radius: 10px;
  user-select: none;
}
</style>
