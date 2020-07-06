<template>
  <div>
    <h1>Exemplo Cadastro de Alunos com VueJS</h1>
    <Aluno></Aluno>
  </div>
</template>

<script>
import Vue from "vue";
import Aluno from "./components/Alunos";

export default Vue.extend({
  components: {
    Aluno
  }
});
</script>

<style>
html,
body,
* {
  font-family: Arial, Helvetica, sans-serif;
  box-sizing: border-box;
}
</style>