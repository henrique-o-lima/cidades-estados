<template>
<apiEstados/>
<Footer />
</template>

<script>
import apiEstados from './components/apiEstados.vue'
import Footer from './components/Footer.vue'
export default {
  components: { apiEstados, Footer }
}
</script>

<style>
  body {
    background: linear-gradient(to right, #2b5876, #4e4376);
    font-family: Arial;
    height: 100%;
  }
</style>
