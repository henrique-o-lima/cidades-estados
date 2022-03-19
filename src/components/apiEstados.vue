<template>
<div class="page">
  <header class="d-flex justify-content-center mt-3">
  <button @click="getEstados" type="button" class="btn btn-outline-light p-2">Mostrar Estados</button>
  
  </header>
  
  <hr />
  <div class="conteudo">
    <div v-for="estados in info" :key="estados">
      <button @click="getCidadesByUf(estados.sigla)" class="estados btn btn-outline-light">
        {{ estados.sigla }}
      </button>
    </div>
  </div>

  <ComponentX
    v-bind:currentUF_="currentUF"
    v-bind:cidadesByUf_="cidadesByUf"
  />
 
</div>
</template>
<script>
import axios from 'axios'
import ComponentX from './Component.vue'
export default{
  components: { ComponentX },
data () {
    return {
      info: null,
      cidadesByUf: null,
      currentUF: null
    }
  },
  mounted () {
    
  },
  methods: {
    getEstados(){
      axios
        .get('https://servicodados.ibge.gov.br/api/v1/localidades/estados')
        .then(response => (this.info = response.data));
    },

    getCidadesByUf(uf){
      this.currentUF = uf;
      axios
      .get('https://servicodados.ibge.gov.br/api/v1/localidades/estados/'+uf+'/municipios')
      .then(response => (this.cidadesByUf = response.data));
      }
  }
}
</script>

<style>
  .page{
    min-height: 100%;
    margin-bottom: 65px;
  }
  .conteudo{
    display: flex;
    margin: auto;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    width: 90%;
    overflow: auto;
  }
  .estados{
    padding: 20px;
    border: 1px solid black;
    box-sizing: border-box;
    margin: 10px;
    width: 100px;
    height: 80px;
    float: left;
    text-align: center;
    justify-content: center;
  }
  .escolhaEstado{
    text-align: center;
  }

</style>