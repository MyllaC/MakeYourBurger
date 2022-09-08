<template>
  <div>
    <p>Componente de mensagem</p>
    <div>
      <form id="burger-form">
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
            <option value="">Brown bread</option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Choose the meat of your burger:</label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Select the meat of your burger:</option>
            <option value="">Beef</option>
          </select>
        </div>
        <div id="additional-container" class="input-container">
          <label id="additional-tittle" for="additional"
            >Choose the additional:</label
          >
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="additional"
              v-model="additional"
              value="salami"
            />
            <span>Salami</span>
          </div>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="additional"
              v-model="additional"
              value="salami"
            />
            <span>Salami</span>
          </div>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="additional"
              v-model="additional"
              value="salami"
            />
            <span>Salami</span>
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
export default {
  name: "BurgerForm",
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
