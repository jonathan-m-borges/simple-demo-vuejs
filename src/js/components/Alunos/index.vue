<template>
  <div>
    <FormAlunos ref="FormAlunos"></FormAlunos>
    <ListaAlunos v-bind:alunos="alunos"></ListaAlunos>
  </div>
</template>

<script>
import FormAlunos from "./FormAlunos.vue";
import ListaAlunos from "./ListaAlunos.vue";
import Aluno from "../../models/Aluno";

export default {
  data() {
    return {
      proxId: 2,
      alunos: []
    };
  },
  methods: {
    carregar(aluno) {
      this.$refs.FormAlunos.carregar(aluno);
    },
    salvar(aluno) {
      if (aluno.id) {
        const index = this.alunos.findIndex(x => x.id==aluno.id);
        const alunos = [...this.alunos]; //cria copia de alunos
        alunos[index] = aluno; //edita o aluno pelo indice
        this.alunos = alunos; //atualiza this.alunos
      }
      else {
        aluno.id = this.proxId;
        this.proxId++;
        this.alunos.push(aluno);
      }
    },
    excluir(id) {
      const index = this.alunos.findIndex(x => x.id==id);
      this.alunos.splice(index, 1);
    }
  },
  components: {
    FormAlunos,
    ListaAlunos
  }
};
</script>

<style>
</style>