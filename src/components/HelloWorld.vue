<template>
  <div id="app">
    <input type="text" id="inputCep" v-model="cep" @keyup="buscar" placeholder="CEP">
    <input type="text" id="inputLogradouro" v-model="endereco.logradouro" placeholder="LOGRADOURO">
    <input type="text" id="inputLocalidade" v-model="endereco.localidade" placeholder="CIDADE">
    <input type="text" id="inputBairro" v-model="endereco.bairro" placeholder="BAIRRO">
    <input type="text" id="inputUf" v-model="endereco.uf" placeholder="UF">
    <input type="text" id="inputNumero" placeholder="NUMERO">
    <input type="text" id="inputComplemento" placeholder="COMPLEMENTO">
  </div>
</template>

<script>
export default {
  data() {
    return {
      cep: "",
      endereco: {}
    };
  },
  methods: {
    buscar: function() {
      var self = this;
      if (/^[0-9]{5}-[0-9]{3}$/.test(this.cep))
      {
        $.getJSON('https://viacep.com.br/ws/'+this.cep+'/json/', function(endereco){
          self.endereco = endereco;
          $(self.$$.numero).focus();
          console.log(endereco);
        });
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
