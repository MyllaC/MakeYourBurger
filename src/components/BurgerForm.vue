<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="burger-form" @submit="createBurger">
        <div class="input-container">
          <label for="name">Client name:</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder="Type your name"
          />
        </div>
        <div class="input-container">
          <label for="bread">Choose your bread:</label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Select the bread:</option>
            <option v-for="bread in breads" :key="bread.id" :value="bread.tipo">
              {{ bread.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Choose the meat of your burger:</label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Select the meat of your burger:</option>
            <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">
              {{ meat.tipo }}
            </option>
          </select>
        </div>
        <div id="additional-container" class="input-container">
          <label id="additional-tittle" for="additionals"
            >Choose the additional:</label
          >
          <div
            v-for="additional in additionalData"
            :key="additional.id"
            class="checkbox-container"
          >
            <input
              type="checkbox"
              name="additionals"
              v-model="additionals"
              :value="additional.tipo"
            />
            <span>{{ additional.tipo }}</span>
          </div>
        </div>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Create your Burger!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from "./Message.vue";
export default {
  name: "BurgerForm",
  data() {
    return {
      breads: null,
      meats: null,
      additionalData: null,
      name: null,
      bread: null,
      meat: null,
      additionals: [],
      status: "Solicitado",
      msg: null,
    };
  },
  methods: {
    async getIngredients() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();
      this.breads = data.paes;
      this.meats = data.carnes;
      this.additionalData = data.opcionais;
    },
    async createBurger(e) {
      e.preventDefault();
      const data = {
        name: this.name,
        meat: this.meat,
        bread: this.bread,
        additionals: Array.from(this.additionals),
        status: "Solicitado",
      };
      const dataJson = JSON.stringify(data);
      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });
      const res = await req.json();

      //colocar uma msg de sistema
      this.msg = "Pedido realizado com sucesso!";

      // clear message
      setTimeout(() => (this.msg = ""), 3000);

      //limpar os campos
      this.name = "";
      this.meat = "";
      this.bread = "";
      this.additionals = "";
    },
  },
  mounted() {
    this.getIngredients();
  },
  components: { Message },
};
</script>

<style scoped>
#burger-form {
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

#additional-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#additional-tittle {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container span,
.checkbox-container input {
  width: auto;
}

.checkbox-container span {
  margin-left: 6px;
  font-weight: bold;
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
  background-color: transparent;
  color: #222;
}
</style>
