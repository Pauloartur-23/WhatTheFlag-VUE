<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <h1>WhatTheFlag</h1>
  <h2>Como jogar?</h2>
  <p>O jogo tem 3 fases</p>
  <p>Cada fase avalia um tipo de informação</p>
  <p>Você terá 30 segundos para passar das 3 fases</p>
  <p>Em casa você deve escolher as bandeiras que atendem ao critério estabelecido</p>

  <button><RouterLink to="/game">INICIAR</RouterLink></button>
</template>

<style scoped>
</style>
