<template>
  <div
    class="caixa"
    :class="{ ativo: hovered }"
    @mouseenter="hovered = true"
    @mouseleave="hovered = false"
  >
    <v-btn
      class="botao"
      @click="avaliar = !avaliar"
    >
      {{ avaliar ? '⭐ Avaliado!' : 'Avaliar' }}
    </v-btn>

    <p class="nota">Nota: {{ avaliar ? 2 : 5 }}</p>
  </div>
</template>

<script setup>
  import { ref } from 'vue'
  const hovered = ref(false)
  const avaliar = ref(false)
</script>

<style scoped>
.caixa {
  width: 200px;
  padding: 30px;
  border-radius: 16px;
  background: #1a1a1a;
  border: 1px solid #333;
  text-align: center;
  transition: all 0.3s ease;
}

.caixa.ativo {
  background: #2a1a00;
  border-color: #ff6400;
  transform: scale(1.05);
}

.nota {
  color: #ff6400;
  font-size: 18px;
  font-weight: bold;
  margin-top: 14px;
}
</style>
