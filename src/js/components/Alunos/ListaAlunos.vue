<template>
  <div>
    <h2>Lista de Alunos</h2>
    <table>
      <thead>
        <tr>
          <th>#</th>
          <th>Nome</th>
          <th>Nota</th>
          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="!possuiAlunos">
          <td colspan="4">Nenhum registro encontrado</td>
        </tr>
        <tr v-for="aluno in alunos" v-bind:key="aluno.id">
          <td>{{aluno.id}}</td>
          <td>{{aluno.nome}}</td>
          <td>{{aluno.nota}}</td>
          <td>
            <a href="#" v-on:click.prevent="editar(aluno)">editar</a> |
            <a href="#" v-on:click.prevent="excluir(aluno.id)">excluir</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  computed: {
    possuiAlunos() {
      return this.alunos && this.alunos.length > 0;
    }
  },
  methods: {
    editar(aluno) {
      this.$parent.carregar(aluno);
    },
    excluir(id) {
      if (confirm("Deseja realmente excluir o aluno?")) {
        this.$parent.excluir(id);
      }
    }
  },
  props: { alunos: Array }
};
</script>

<style scoped>
table {
  border-collapse: collapse;
  width: 100%;
}
th {
  background: black;
  color: white;
}
td,
th {
  border: 1px solid #ddd;
  padding: 8px;
}
tr:nth-child(even) {
  background: #ddd;
}
tr:hover {
  background-color: #aaa;
}
</style>