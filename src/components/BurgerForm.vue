<template>
  <div>
    <p>Componente de mensagen</p>
    <div>
      <form id="burger-form">
        <div class="input-container">
          <label for="Name">Nome do Cliente:</label>
          <input
            type="text"
            name="name"
            id="name"
            v-model="name"
            placeholder="Digite o seu nome"
          />
        </div>
        <div class="input-container">
          <label for="bread">Escolha o Pão:</label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione seu pão</option>
            <option value="integral">Integral</option>
          </select>
        </div>

        <div class="input-container">
          <label for="beef">Escolha a carne do seu Burger</label>
          <select name="beef" id="beef" v-model="bread">
            <option value="">Selecione sua Carne</option>
            <option value="maminha">maminha</option>
          </select>
        </div>

        <div id="options-container" class="input-container">
          <label class="options-title" for="options"
            >Selecione os opcionais:</label
          >
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="options"
              v-model="options"
              value="Salame"
            />
            <span>Salame</span>
          </div>
        </div>

        <div class="input-container">
          <input type="submit" value="Criar meu Burger!" class="submit-btn" />
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  name: "BurgerForm",
  data() {
    return {};
  },
};
</script>
<style scoped>
#burger-form {
  width: 25rem;
  margin: 0 auto;
}
.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 1.25rem;
}
label {
  font-weight: bold;
  margin-bottom: 1rem;
  padding: 0.313rem 0.625rem;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 0.313rem 0.625rem;
  width: 18.75rem;
}
.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 1.25rem;
}
#options-container {
  flex-direction: row;
  flex-wrap: wrap;
}
.options-title {
  width: 100%;
}

.checkbox-container span,
.checkbox-container input {
  width: auto;
}
.checkbox-container span {
  margin-left: 0.375rem;
  font-weight: bold;
}

.submit-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 0.625rem;
  font-size: 1rem;
  margin: 0 auto;
  cursor: pointer;
}
.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>