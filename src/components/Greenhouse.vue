<template>
  <div class="greenhouse-card">
    <h1>{{ greenhouse.name }}</h1>
    <h3>Temperature: {{ greenhouse.temperature }} &deg;</h3>
    <form @submit.prevent="changeTemp">
      <input type="text" placeholder="New temperature" aria-label="New Temperature" v-model="newTemp"/>
      <button type="submit">Change Temperature</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Greenhouse',
  props: {
    greenhouse: {}
  },
  data: () => ({
    newTemp: '',
  }),
  methods: {
    changeTemp() {
      const tmp = parseInt(this.newTemp);

      if (!isNaN(tmp)) {
        this.$emit("changeTemp", tmp)
      }
    },
  }
}
</script>

<style scoped>
.greenhouse-card {
  max-width: 30vw;
  background-color: #f0f0f0;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}
</style>