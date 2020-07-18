<template>
  <div>
    <h1></h1>
    <Titulo text="Alunos"/>
    <div>
      <input type="text" placeholder="Nome do Aluno" v-model="nome" @keyup.enter="addAluno()">
      <button class="btn btn-input" @click="addAluno()">Adicionar</button>
    </div>

    <table>
      <thead>
        <th>Matrícula</th>
        <th>Nome</th>
        <th>Opções</th>
      </thead>
      <tbody v-if="alunos.length">
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{aluno.id}}</td>
          <td>{{aluno.nome}} {{aluno.sobrenome}}</td>
          <td>
            <button class="btn btn-danger" @click="remover(aluno)">Remover</button>
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
        <tr>
          <td colspan="3">
            Nenhum aluno encontrado :(
          </td>
        </tr>
      </tfoot>
    </table>

  </div>
</template>

<script>
import Titulo from '../_shared/Titulo';

const baseUrl = "http://localhost:3000";

export default {
  components:{
    Titulo
  },
  data(){
    return{
      titulo: "Alunos",
      nome: '',
      alunos: []
    }
  },
  created(){
    this.$http
    .get(`${baseUrl}/alunos`)
    .then(response => response.json())
    .then(alunos => this.alunos = alunos)
  },
  props: {},
  methods: {
    addAluno(){
      let _aluno = { 
        nome: this.nome,
        sobrenome: ""
      }

      this.$http
        .post(`${baseUrl}/alunos`, _aluno)
        .then(response => response.json())
        .then(alunoRetorno =>{
          this.alunos.push(alunoRetorno);
          this.nome = '';
        })

    },
    remover(aluno){
      this.$http
        .delete(`${baseUrl}/alunos/${aluno.id}`)
        .then(() => {
          let indice = this.alunos.indexOf(aluno);
          this.alunos.splice(indice, 1);
        })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

input{
  width: calc(100% - 195px);
  border: 0px;
  padding: 20px;
  font-size: 1.3em;
  color: #687f7f;
  margin-bottom: 10px;
  display: inline;
}

.btn-input{
  width: 140px;
  margin-left: 10px;
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  display: inline;
  background-color: rgb(116, 115, 116);
}

.btn-input:hover{
  padding: 20px;
  margin:0px;
  margin-left: 10px;
  bottom: 0px;
}
</style>
