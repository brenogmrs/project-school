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
            <td>{{prof.nome}} {{prof.sobrenome}}</td>
            <td>
                3
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

export default {
    components:{
        Titulo
    },
    data(){
        return {
            professores:[
                {
                    id: 1,
                    nome: 'Vinicius'
                },
                {
                    id: 2,
                    nome: 'Paula'
                },
                {
                    id: 3,
                    nome: 'Luna'
                },
            ]
        }
    }
}
</script>
<style lang="">
    
</style>