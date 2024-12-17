<template>
  <p class="validation-message">
    {{ mensagem }}
  </p>
</template>
  
  <script>
  export default {
    props: {
      mensagem: {
        type: String,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
.validation-message {
  color: red;
  font-size: 0.875em;
  margin-top: -8px;
  margin-bottom: 10px;
}
</style>