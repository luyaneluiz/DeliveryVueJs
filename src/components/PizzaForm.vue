<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="pizza-form" @submit="createPizza">
        <div class="input-container">
          <label for="nome">Nome do cliente:</label>
          <input
            type="text"
            name="nome"
            id="nome"
            v-model="nome"
            placeholder="Digite seu nome"
          />
        </div>
        <div class="input-container">
          <label for="borda">Escolha a borda:</label>
          <select name="borda" id="borda" v-model="borda">
            <option value="">Selecione a borda</option>
            <option v-for="borda in bordas" :key="borda.id" :value="borda.tipo">
              {{ borda.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="sabor">Escolha a sabor:</label>
          <select name="sabor" id="sabor" v-model="sabor">
            <option value="">Selecione o sabor</option>
            <option
              v-for="sabor in sabores"
              :key="sabor.id"
              :value="sabor.tipo"
            >
              {{ sabor.tipo }}
            </option>
          </select>
        </div>
        <div id="#adicionais-container" class="input-container">
          <label id="adicionais-title" for="adicionais">Adicionais:</label>
          <div
            class="checkbox-container"
            v-for="adiconal in adicionaisdata"
            :key="adiconal.id"
          >
            <input
              type="checkbox"
              name="adicionais"
              v-model="adicionais"
              :value="adiconal.tipo"
            />
            <span>{{ adiconal.tipo }}</span>
          </div>
        </div>

        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar minha Pizza" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from "./Message.vue";
export default {
  name: "PizzaForm",
  data() {
    return {
      bordas: null,
      sabores: null,
      adicionaisdata: null,
      nome: null,
      borda: null,
      sabor: null,
      adicionais: [],
      status: "Solicitado",
      msg: null,
    };
  },
  components: {
    Message,
  },
  methods: {
    async getIngredientes() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.bordas = data.bordas;
      this.sabores = data.sabores;
      this.adicionaisdata = data.adicionais;
    },
    async createPizza(e) {
      e.preventDefault();

      const data = {
        nome: this.nome,
        sabor: this.sabor,
        borda: this.borda,
        adicionais: Array.from(this.adicionais),
        status: "Solicitado",
      };

      console.log(data);

      const dataJson = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/pizzas", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();

      this.msg = `Pedido Nº ${res.id} realizado com sucesso!`;

      setTimeout(() => (this.msg = ""), 3000);

      this.nome = "";
      this.borda = "";
      this.sabor = "";
      this.adicionais = "";
    },
  },
  mounted() {
    this.getIngredientes();
  },
};
</script>

<style scoped>
#pizza-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#adicionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#adicionais-title {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: center;
  width: 50%;
  margin-bottom: 20px;
  justify-content: flex-start;
}

.checkbox-container span,
.checkbox-container input {
  width: auto;
}

.checkbox-container span {
  font-weight: bold;
  margin-left: 6px;
}

.submit-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.submit-btn:hover {
  background-color: rgba(0, 0, 0, 0.378);
  color: #222;
}
</style>
