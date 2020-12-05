<template>
  <div class="greenhouse-card">
    <h1>{{ greenhouse.name }}</h1>
    <h3>Temperature: {{ greenhouse.temperature }} &deg;</h3>
    <button @click="increase">Increase Temperature</button>
    <button @click="decrease">Decrease Temperature</button>
  </div>
</template>

<script>
export default {
  name: 'Greenhouse',
  props: {
    greenhouse: {}
  },
  methods: {
    increase() {
      this.$emit("increase")
    },
    decrease() {
      this.$emit("decrease")
    }
  }
}
</script>

<style scoped>
.greenhouse-card {
  max-width: 30vw;
  background-color: #f0f0f0;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}
</style>