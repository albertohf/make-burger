<template>
  <Message :msg="msg" v-show="msg" />
  <div id="burger-table">
    <div>
      <div id="burger-table-header">
        <div id="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
        <div class="order-number">{{ burger.id }}</div>
        <div>{{ burger.nome }}</div>
        <div>{{ burger.pao }}</div>
        <div>{{ burger.carne }}</div>
        <div>
          <ul>
            <li v-for="(opcional, index) in burger.opcionais" :key="index">
              {{ opcional }}
            </li>
          </ul>
        </div>
        <div>
          <select
            name="status"
            class="status"
            @change="updateBurger($event, burger.id)"
          >
            <option value="">Selecione</option>
            <option
              v-for="s in status"
              :key="s.id"
              :value="s.tipo"
              :selected="burger.status == s.tipo"
            >
              {{ s.tipo }}
            </option>
          </select>
          <button class="delete-btn" @click="deleteBurger(burger.id)">
            Cancelar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Message from "./Message";
export default {
  name: "Dashboard",
  components: {
    Message,
  },
  data() {
    return {
      burgers: null,
      burgerId: null,
      status: [],
      msg: null,
    };
  },
  methods: {
    async getRequests() {
      const req = await fetch("http://localhost:3000/burgers");

      const data = await req.json();

      this.burgers = data;

      //resgatar status
      this.getStatus();
    },
    async getStatus() {
      const req = await fetch("http://localhost:3000/status");

      const data = await req.json();

      this.status = data;
    },
    async deleteBurger(id) {
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE",
      });
      const res = await req.json();
      //msg

      this.getRequests();

      //msg do sistema
      this.msg = `Pedido Nº ${id} Cancelado com sucesso!`;
      // limpar msg sistema
      setTimeout(() => {
        this.msg = "";
      }, 4000);
    },
    async updateBurger(event, id) {
      const option = event.target.value;

      const dataJson = JSON.stringify({ status: option });

      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: { "content-Type": "application/json" },
        body: dataJson,
      });
      const res = await req.json();

      //msg do sistema
      this.msg = `Pedido Nº ${res.id} foi atualizado para ${res.status}!`;
      // limpar msg sistema
      setTimeout(() => {
        this.msg = "";
      }, 4000);
    },
  },
  mounted() {
    this.getRequests();
  },
};
</script>
<style scoped>
#burger-table {
  max-width: 75rem;
  margin: 0 auto;
}
#burger-table-header,
#burger-table-rows,
.burger-table-row {
  display: flex;
  flex-wrap: wrap;
}
#burger-table-header {
  font-weight: bold;
  padding: 0.75rem;
  border-bottom: 3px solid #333;
}
.burger-table-row {
  width: 100%;
  padding: 0.75rem;
  border-bottom: 1px solid #ccc;
}
#burger-table-header div,
.burger-table-row div {
  width: 19%;
}
#burger-table-header .order-id,
.burger-table-row .order-number {
  width: 5%;
}
select {
  padding: 0.75rem 0.375rem;
  margin-right: 0.75rem;
}
.delete-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 0.625rem;
  font-size: 1rem;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.delete-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>
