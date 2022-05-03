<template>
  <div class="placar">
    <h2>Total: {{ total }}</h2>
    <div class="two">
      <h3>Vitórias: {{ victory }}</h3>
      <h3>Derrotas: {{ looses }}</h3>
    </div>
    <div class="buttons">
      <button @click="$emit('onRestart')">Reiniciar</button>
      <button @click="$emit('onReset')">Zerar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "PlacarDisplay",
  props: {
    total: {
      type: Number,
      required: true,
    },
    victory: {
      type: Number,
      required: true,
    },
    looses: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style>
.placar {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 1rem;
}

.placar .two {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.placar .two h3 {
  margin: 0.5rem;
}

.buttons {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.buttons button {
  border: none;
  background: #26d0ce; /* fallback for old browsers */

  border-radius: 0.5rem;
  color: #eee;
  margin: 0.5rem;
  padding: 0.5rem;
}

.buttons button:hover {
  background: #188381; /* fallback for old browsers */
}

.buttons button:active {
  background: #2efffc; /* fallback for old browsers */
}
</style>
