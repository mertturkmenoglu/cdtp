<template>
  <div>
    <div v-if="greenhouses.length > 0">
      <div v-for="(greenhouse, idx) in greenhouses" :key="idx">
        <Greenhouse
            :greenhouse="greenhouse"
            class="mb-3"
            @changeTemp="(tmp) => change(greenhouse.name, tmp)"
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
    greenhouses: [],
  }),
  mounted() {
    this.fetchGreenhouses();
  },
  methods: {
    async fetchGreenhouses() {
      const URL = 'https://cdtp-backend.herokuapp.com/api/all'
      const response = await fetch(URL);
      const data = await response.json();

      if (!data['status_code']) {
        this.greenhouses = data.greenhouses;
      }
    },
    async change(name, tmp) {
      const BASE_URL = 'https://cdtp-backend.herokuapp.com/api'
      const URL = `${BASE_URL}/${name}`
      const requestOptions = {
        method: 'PUT',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({'temperature': tmp })
      }

      const response = await fetch(URL, requestOptions)
      const data =  await response.json()

      if (!data['status_code']) {
        await this.fetchGreenhouses()
      }
    },
  },
}
</script>

<style scoped>
.mb-3 {
  margin-bottom: 3em;
}
</style>