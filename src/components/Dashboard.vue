<template>
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
      <div class="burger-table-row">
        <div class="order-number">1</div>
        <div>Nome</div>
        <div>pao</div>
        <div>carne</div>
        <div>
          <ul>
            <li>salame</li>
            <li>tomate</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status">
            <option value="">Selecione</option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Dashboard",
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
