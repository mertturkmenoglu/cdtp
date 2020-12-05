<template>
  <div class="home">
    <Header />
    <main>
      <GreenhouseDisplay />
    </main>
  </div>
</template>

<script>
import Header from "@/components/Header";
import GreenhouseDisplay from "@/components/GreenhouseDisplay";

export default {
  name: 'Home',
  components: {GreenhouseDisplay, Header},
}
</script>
