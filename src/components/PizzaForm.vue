<template>
  <Message :msg="msg" v-show="msg" />
  <!-- <div>
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
            <option v-for="borda in bordas" :key="borda.id" :value="borda.name">
              {{ borda.name }}
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
              :value="sabor.name"
            >
              {{ sabor.name }}
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
              :value="adiconal.name"
            />
            <span>{{ adiconal.name }}</span>
          </div>
        </div>

        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar minha Pizza" />
        </div>
      </form>
    </div> -->
  <div class="details__container">
    <a name="selectSabor">
      <div class="title" v-for="sabor in sabores" :key="sabor.id">
        <h1 v-if="sabor.id == selected">{{ sabor.tipo }}</h1>
        <p v-if="sabor.id == selected">{{ sabor.label }}</p>
      </div>
      <div class="info__container">
        <div class="options">
          <select name="borda" id="borda" v-model="borda">
            <option :value="false" :selected="borda">Change board</option>
            <option v-for="borda in bordas" :key="borda.id" :value="borda.name">
              {{ borda.name }}
            </option>
          </select>
          <button v-if="!showAditionals" v-on:click="showAditionals = true">
            <i class="bx bx-plus"></i>
            Aditionals
          </button>
          <button v-if="showAditionals" v-on:click="showAditionals = false">
            <i class="bx bx-minus"></i>
            Aditionals
          </button>
          <div v-if="showAditionals" class="aditionals__container">
            <label
              class="checkbox"
              v-for="adiconal in adicionaisdata"
              :key="adiconal.id"
            >
              <input
                type="checkbox"
                name="adicionais"
                v-model="adicionais"
                :value="adiconal.name"
              />
              <span>{{ adiconal.name }}</span>
            </label>
          </div>
        </div>
        <div class="size">
          <span class="s">
            <input type="radio" id="s" name="size" hidden />
            <label for="s">S</label>
          </span>
          <span class="m">
            <input type="radio" id="m" name="size" checked hidden />
            <label for="m">M</label>
          </span>
          <span class="l">
            <input type="radio" id="l" name="size" hidden />
            <label for="l">L</label>
          </span>
        </div>
        <div class="request">
          <div class="request__name">
            <input type="text" name="nome" id="nome" v-model="nome" required />
            <label for="nome">Nome completo</label>
          </div>
          <div class="amount" v-bind="amount">
            <button @click="amount--">-</button>
            <div>{{ amount }}</div>
            <button>+</button>
          </div>
          <input type="submit" class="submit-btn" value="Request" />
        </div>
      </div>
    </a>
  </div>

  <div class="select__sabor" v-bind="sabor">
    <div class="select__container">
      <label :for="sabor.id" v-for="sabor in sabores" :key="sabor.id">
        <input
          type="radio"
          name="sabor"
          :id="sabor.id"
          hidden
          @click="updateSelected"
        />
        <img :src="sabor.img" alt="" />
      </label>
    </div>
  </div>
</template>

<script>
import Message from "./Message.vue";
export default {
  name: "PizzaForm",
  data() {
    return {
      selected: 1,
      bordas: null,
      sabores: null,
      adicionaisdata: null,
      nome: null,
      borda: null,
      sabor: null,
      adicionais: [],
      status: "Solicitado",
      msg: null,
      showAditionals: false,
      amount: 0,
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
    async setSelected() {
      let inputsSelect = document.querySelectorAll('[name="sabor"]');

      inputsSelect.forEach((input) => {
        if (input.id == this.selected) {
          input.setAttribute("checked", true);

          let container = input.closest(".select__container");
          console.log(container);

          switch (input.id) {
            case "1":
              container.style.transform = "translateX(20vw)";
              break;
            case "2":
              container.style.transform = "translateX(-20vw)";
              break;
            case "3":
              container.style.transform = "translateX(-60vw)";
              break;
            case "4":
              container.style.transform = "translateX(-100vw)";
              break;
            case "5":
              container.style.transform = "translateX(-140vw)";
              break;
          }
        }
      });
    },
    async updateSelected() {
      let inputsSelect = document.querySelectorAll('[name="sabor"]');

      inputsSelect.forEach((input) => {
        if (input.checked == true) {
          this.selected = parseInt(input.id);
        }
      });
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
  updated() {
    this.setSelected();
  },
};
</script>

<style scoped>
.details__container {
  padding: 0 100px;
}
.title {
  text-align: center;
}
.title h1 {
  font-family: "Fjalla One", sans-serif;
  margin-bottom: 10px;
}
.title p {
  font-family: "Poppins", sans-serif;
}
.info__container {
  display: grid;
  grid-template-columns: 32% 30% 32%;
  gap: 3%;
}
.options {
  display: flex;
  flex-direction: column;
  gap: 10px;
  position: relative;
}
.options #borda {
  background: linear-gradient(45deg, #e9e4e48a, #e8cfcf63);
  backdrop-filter: blur(12px);
  border: none;
  border-radius: 8px;
  padding: 8px;
  width: 150px;
  outline: none;
}
.options button {
  width: 150px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 50px;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 5px;
  cursor: pointer;
  z-index: 2;
}
.aditionals__container {
  position: absolute;
  bottom: -115%;
  background: white;
  border-radius: 0 0 15px 15px;
  padding: 20px 15px 15px 15px;
  width: 150px;
  z-index: 1;
  border: 1px solid #ccc;
}
.aditionals__container .checkbox {
  display: flex;
  gap: 5%;
  font-size: 15px;
  cursor: pointer;
}
.size {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 3%;
  margin: 20px 0;
}
.size label {
  background-color: #f8f8f8;
  border: 1px solid #ccc;
  border-radius: 50%;
  width: 45px;
  height: 45px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.5s ease-in-out;
  color: #626262;
}
.size input:checked + label {
  background-color: #fff;
  width: 55px;
  height: 55px;
  font-size: 20px;
  color: #373737;
}
.request__name {
  position: relative;
}
.request__name input {
  border: solid 1px #ccc;
  border-radius: 1rem;
  background: none;
  padding: 1em;
  transition: 150ms cubic-bezier(0.4, 0, 0.2, 1);
}
.request__name label {
  position: absolute;
  left: 16px;
  top: 13px;
  color: rgb(117, 117, 117);
  font-size: 14px;
  padding: 0 0.1em;
  pointer-events: none;
  transition: 150ms cubic-bezier(0.4, 0, 0.2, 1);
}
.request__name input:focus {
  outline: none;
  border: solid 1px #626060;
  border-radius: 1rem;
  background: none;
  padding: 1rem;
  transition: 150ms cubic-bezier(0.4, 0, 0.2, 1);
}
.request__name input:focus + label,
.request__name input:valid + label {
  background-color: #fff;
  padding: 0 0.2em;
  color: #626060;
  top: -10px;
}
.amount {
  display: flex;
  padding: 15px 0;
}
.amount button {
  width: 30px;
  height: 30px;
  background-color: transparent;
  border: 1px solid #ccc;
  border-radius: 50%;
  cursor: pointer;
}
.amount div {
  width: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 15px;
}

.submit-btn {
  padding: 8px 15px;
  border-radius: 15px;
  background-color: #f3f3f3;
  border: 1px solid #ccc;
  color: #626262;
}

.select__sabor {
  overflow: hidden;
  height: 56vh;
  width: 100%;
  position: relative;
}
.select__sabor label {
  cursor: pointer;
}

.select__container {
  display: flex;
  transition: transform 0.7s ease-in-out;
  transform: translateX(0);
  align-items: baseline;
  justify-content: space-between;
}

.select__container img {
  object-fit: cover;
  width: 40vw;
  transition: all 0.5s ease-in-out;
}
.select__container input:checked + img {
  object-fit: cover;
  object-position: top;
  width: 50vw;
  margin: 0 5vw;
}
</style>
