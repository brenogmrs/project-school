<template>
    <div>
        <Titulo text="Professores"/>

        <table>
        <thead>
            <th>Codigo</th>
            <th>Nome</th>
            <th>Qtd. Alunos</th>
        </thead>
        <tbody v-if="professores.length">
            <tr v-for="(prof, index) in professores" :key="index">
            <td>{{prof.id}}</td>
            <router-link to="/alunos" tag="td" style="cursor: pointer;">
                {{prof.nome}} {{prof.sobrenome}}
            </router-link>
            
            <td>
               {{prof.qtdAlunos}}
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
        return {
            alunos:[],
            professores:[]
        }
    },
    created(){
        this.$http
            .get(`${baseUrl}/alunos`)
            .then(response => response.json())
            .then(alunos => {
                this.alunos = alunos;
                this.getProfessores();
            })
    },
    props: {

    },
    methods: {
        getProfQtdAlunos(){
            this.professores.forEach((prof, index) => {
                prof = {
                    id: prof.id,
                    nome: prof.nome,
                    qtdAlunos: this.alunos.filter(
                        aluno => aluno.professor.id == prof.id
                    ).length
                }
                this.professores[index] = prof
            });
        },
        getProfessores(){
            this.$http
                .get(`${baseUrl}/professores`)
                .then(response => response.json())
                .then(professor => {
                    this.professores = professor;
                    this.getProfQtdAlunos();
                })
        }
    },
}
</script>
<style lang="">
    
</style>