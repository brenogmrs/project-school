<template>
  <div id="app">
    <Nav />
    <div class="margin-principal">
      <Alunos />
    </div>
  </div>
</template>

<script>
import Alunos from './components/Aluno/Alunos.vue'
import Nav from './components/_nav/Nav.vue'


export default {
  name: 'App',
  components: {
    Alunos,
    Nav
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');
body{
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body html{
  margin: 0;
  height: 100%;
}

.margin-principal{
  width: 50%;
  margin: auto;
}

#app {
  width: 100%;
}

.btn-danger{
  background-color: #fa4430;
}

.btn{
  padding: 10px 20px;
  cursor: pointer;
  border: 1px solid black;
  color: white;
  font-weight: bold;
  border-radius: 5px;
  border-bottom: 2px solid black;
}

.btn:hover{
  text-shadow: 1px 1px 1px black;
  margin-top: 1px;
  border-bottom: 1px solid black;
}

table{
  margin: 0px;
  padding: 0px;
  list-style-type: none;
  width: 100%;
}

table tr td {
  font-size: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  padding: 20px 20px;
  color: #3e5252;
}

table thead th{
  background-color: rgb(184, 208, 216)!important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}

.col-pequeno{
  width: 5%;
}

</style>
