<template>
  <div class="agenda-list">
    <h2>Contatos</h2>
    <ul>
      <li v-for="(contato, index) in contatos" :key="index">
        {{ contato.nome }} - {{ contato.email }} - {{ contato.telefone }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    contatos: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.agenda-list {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.agenda-list h2 {
  font-size: 1.5em;
  margin-bottom: 10px;
  color: #333;
}

.agenda-list ul {
  list-style: none;
  padding: 0;
}

.agenda-list li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

.agenda-list li:last-child {
  border-bottom: none;
}
</style>