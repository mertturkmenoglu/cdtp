<template>
  <div>
    <div v-if="greenhouses.length > 0">
      <div v-for="(greenhouse, idx) in greenhouses" :key="idx">
        <Greenhouse
            :greenhouse="greenhouse"
            class="mb-3"
            @changeTemp="(tmp) => change(idx, greenhouse.name, tmp)"
        />
      </div>
    </div>
    <div v-else>
      <h3>No data available</h3>
    </div>
  </div>
</template>

<script>
import Greenhouse from "@/components/Greenhouse";

export default {
  name: 'GreenhouseDisplay',
  components: {Greenhouse},
  data: () => ({
    // HARDCODED DATA FOR TESTING
    // TODO: REMOVE THIS PART AFTER BACKEND IMPLEMENTATION
    greenhouses: [
      {
        "name": "Greenhouse A",
        "temperature": 32
      },
      {
        "name": "Greenhouse B",
        "temperature": 36
      },
      {
        "name": "Greenhouse C",
        "temperature": 34
      }
    ],
  }),
  mounted() {
    this.fetchGreenhouses();
  },
  methods: {
    async fetchGreenhouses() {
      // COMMENTED OUT FOR TEST PURPOSES
      // TODO: UNCOMMENT THIS PART AFTER BACKEND IMPLEMENTATION
      // TODO: CHANGE THIS URL AFTER BACKEND IMPLEMENTATION
      //const URL = 'REST_API_URL'
      //const response = await fetch(URL);
      //const data = await response.json();

      //console.log(data)
      // if (data['status_code'] !== 200) {
      //   return;
      // }

      //this.greenhouses = data.greenhouses;
    },
    change(idx, name, tmp) {
      // TODO: MAKE API CALLS
      this.greenhouses[idx].temperature = tmp;
      console.log(`${name} temperature changed. New temperature: ${this.greenhouses[idx].temperature}`);
    },
  },
}
</script>

<style scoped>
.mb-3 {
  margin-bottom: 3em;
}
</style>