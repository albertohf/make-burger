<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="burger-form" @submit="createBurger">
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
            <option
              v-for="bread in breadsData"
              :key="bread.id"
              :value="bread.tipo"
            >
              {{ bread.tipo }}
            </option>
          </select>
        </div>

        <div class="input-container">
          <label for="beef">Escolha a carne do seu Burger</label>
          <select name="beef" id="beef" v-model="meat">
            <option value="">Selecione sua Carne</option>
            <option v-for="meat in meatsData" :key="meat.id" :value="meat.tipo">
              {{ meat.tipo }}
            </option>
          </select>
        </div>

        <div id="options-container" class="input-container">
          <label class="options-title" for="options"
            >Selecione os opcionais:</label
          >
          <div
            class="checkbox-container"
            v-for="choice in choicesData"
            :key="choice.id"
          >
            <input
              type="checkbox"
              name="choices"
              v-model="choices"
              :value="choice.tipo"
            />
            <span>{{ choice.tipo }}</span>
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
import Message from "./Message";
export default {
  name: "BurgerForm",
  components: {
    Message,
  },
  data() {
    return {
      breadsData: null,
      meatsData: null,
      choicesData: null,
      name: null,
      bread: null,
      meat: null,
      choices: [],
      msg: null,
    };
  },
  methods: {
    async getIngredients() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.breadsData = data.paes;
      this.meatsData = data.carnes;
      this.choicesData = data.opcionais;
    },
    async createBurger(e) {
      e.preventDefault();

      const data = {
        nome: this.name,
        carnes: this.meat,
        pao: this.bread,
        opcionais: Array.from(this.choices),
        status: "Solicitado",
      };

      const dataJson = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();

      //limpando os campos
      this.name = "";
      this.meat = "";
      this.bread = "";
      this.choices = "";

      //msg do sistema
      this.msg = `Pedido Nº ${res.id} Realizado com sucesso!`;
      // limpar msg sistema
      setTimeout(() => {
        this.msg = "";
      }, 4000);
    },
  },
  mounted() {
    this.getIngredients();
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