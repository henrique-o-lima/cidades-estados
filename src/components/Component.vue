<template>
   <hr />
  <div v-if="currentUF_ !== null" class="cidades">
  <h1>Cidades em <strong>{{ currentUF_ }}</strong>:</h1>
  <table class="table table-dark">
  <thead>
    <tr>
    <th scope="col">ID</th>
    <th scope="col">Nome</th>
    <th scope="col">Mesorregião</th>
    <th scope="col">UF</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="cidade in cidadesByUf_" :key="cidade" >
      <th scope="row">{{ cidade.id }}</th>
      <td>{{ cidade.nome }}</td>
      <td>{{ cidade.microrregiao.nome }}</td>
      <td>{{ cidade.microrregiao.mesorregiao.UF.sigla}}</td>
    </tr>
  </tbody>  
  </table>
  </div>
<div v-else class="escolhaEstado">
  <h1>Escolha um estado.</h1>
</div>

</template>

<script>
export default {
    props: [
        'currentUF_',
        'cidadesByUf_'
    ]
}
</script>

<style>

</style>