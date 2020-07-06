<template>
  <form id="form-alunos" v-on:submit.prevent="onSubmit">
    <h2>Cadastrar aluno</h2>
    <p>
      <label for="nome">Nome:</label>
      <input name="nome" v-model="nome" />
    </p>
    <p>
      <label for="nota">Nota:</label>
      <input name="nota" v-model="nota" type="number" />
    </p>
    <p>
      <div class="error">{{errorMessage}}</div>
      <input type="submit" value="Salvar" />
    </p>
  </form>
</template>

<script>
import Aluno from '../../models/Aluno';

export default {
  data() {
    return {
      errorMessage: "",
      id: "",
      nome: "",
      nota: ""
    };
  },
  methods: {
    onSubmit(e) {
      this.errorMessage = "";
      if (!this.nome) {
        this.errorMessage = "Nome é obrigatório"
        return;
      }
      const aluno = new Aluno(this.id, this.nome, this.nota);
      this.$parent.salvar(aluno);
      this.id = 0;
      this.nome = "";
      this.nota = "";
    },
    carregar(aluno) {
      this.id = aluno.id;
      this.nome = aluno.nome;
      this.nota = aluno.nota;
    }
  }
};
</script>

<style>
.error {
  color: red;
}

#form-alunos {
  border: 1px solid #aaa;
  padding: 10px;
}
label {
  display: block;
}
</style>