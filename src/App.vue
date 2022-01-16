<template>
  <div class="row">
    <h2 class="title">Conversor de Moedas</h2>
    <Conversor from-currency="USD" to-currency="BRL" />
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";

export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: centers;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

.row {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

</style>
