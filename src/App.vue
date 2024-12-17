<template>
  <div id="app">
    <h1>Agenda</h1>
    <AgendaForm @adicionarContato="adicionaContato" />
    <AgendaList :contatos="contatos" />
  </div>
</template>

<script>
import AgendaForm from "./components/AgendaForm.vue";
import AgendaList from "./components/AgendaList.vue";

export default {
  components: { AgendaForm, AgendaList },
  data() {
    return {
      contatos: []
    };
  },
  methods: {
    adicionaContato(contato) {
      this.contatos.push(contato);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}

#app h1 {
  font-size: 2em;
  margin-bottom: 20px;
  color: #007BFF;
}
</style>