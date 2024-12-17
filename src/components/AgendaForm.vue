<template>
  <div class="agenda-form">
    <h2>Adicionar Contato</h2>
    <form @submit.prevent="adicionarAgenda">
    
      <div>
        <label>Nome:</label>
        <input id="nome" v-model="nome" type="text" />
        <ValidationMessage v-if="errors.nome" :mensagem="errors.nome" />
      </div>
  
      <div>
        <label>Email:</label>
        <input id="email" v-model="email" type="email" />
        <ValidationMessage v-if="errors.email" :mensagem="errors.email" />
      </div>
  
      <div>
        <label>Telefone:</label>
        <input id="telefone" v-model="telefone" type="text" />
        <ValidationMessage v-if="errors.telefone" :mensagem="errors.telefone" />
      </div>
  
      <button type="submit">Adicionar</button>
    </form>
  </div>
</template>

<script>
import ValidationMessage from "./ValidationMessage.vue";
import axios from "axios";

export default {
  components: { ValidationMessage },
  data() {
    return {
      nome: "",
      email: "",
      telefone: "",
      errors: {}
    };
  },
  methods: {
    validateForm() {
      const errors = {};
      if (!this.nome) errors.nome = "O nome é obrigatório.";
      if (!this.email || !/^[^@\s]+@[^@\s]+\.[^@\s]+$/.test(this.email)) {
        errors.email = "Um email válido é obrigatório.";
      }
      return errors;
    },
    async adicionarAgenda() {
      this.errors = this.validateForm();
      if (Object.keys(this.errors).length === 0) {
        try {
          await axios.post("http://localhost:5179/agenda", {
            nome: this.nome,
            email: this.email,
            telefone: this.telefone
          });
          this.$emit("adicionarContato", { nome: this.nome, email: this.email, telefone: this.telefone });
          this.nome = "";
          this.email = "";
          this.telefone = "";
        } catch (error) {
          console.error("Erro ao enviar dados ao servidor:", error);
        }
      }
    }
  }
};
</script>

<style scoped>
.agenda-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.agenda-form h2 {
  font-size: 1.5em;
  margin-bottom: 10px;
  color: #333;
}

.agenda-form label {
  display: block;
  margin: 5px 0;
  font-weight: bold;
}

.agenda-form input {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1em;
}

.agenda-form button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 4px;
  font-size: 1em;
  cursor: pointer;
}

.agenda-form button:hover {
  background-color: #0056b3;
}
</style>