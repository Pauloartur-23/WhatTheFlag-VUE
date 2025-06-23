<script setup>
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
]

function certo(id) {
  if (id === 1 || id === 2 || id === 3) {
    alert('Acertou!');
  } else {
    alert('Errou! Tente novamente.');
  }
}
</script>

<template>
  <div class="game-view">
    <h2>00:30</h2>
    <div class="conteiner">
      <h1>O idioma é espanhol?</h1>
      <ul>
        <li v-for="bandeira in Bandeiras" :key="bandeira.id" @click="certo(bandeira.id)"><img :src="bandeira.imagem" alt=""></li>
      </ul>
      <p>Acertos 0 / 3</p>
    </div>
  </div>
</template>

<style scoped>
.game-view {
  height: 100vh;
}
.conteiner {
  background-color: #f0f0f0;
}

h1 {
  text-align: center;
  font-size: 2em;
  padding-top: 30px;

}

h2 {
  background-color: #cca5ff;
  text-align: center;
  font-size: 4em;
  padding: 1vw 0;
}

p {
  text-align: center;
  font-size: 2em;
  margin-top: 20px;
}

ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding: 0 38vw;
}

li {
  list-style: none;
  margin: 10px;
}

img {
  width: 100px;
  height: 100px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}
</style>