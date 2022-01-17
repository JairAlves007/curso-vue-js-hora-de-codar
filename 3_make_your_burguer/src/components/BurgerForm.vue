<template>
  <div>
    <Message :msg="msg" v-show="msg" />

    <div>
      <form id="burger-form" @submit="createBurger">
        <div class="input-container">
          <label for="name">Nome Do Cliente</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder="Digite seu nome"
          />
        </div>

        <div class="input-container">
          <label for="pao">Escolha o Pão</label>

          <select name="pao" id="pao" v-model="pao">
            <option value="" selected>Selecione o seu pão</option>
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
          </select>
        </div>

        <div class="input-container">
          <label for="carne">Escolha A Carne</label>

          <select name="carne" id="carne" v-model="carne">
            <option value="" selected>Selecione o tipo de carne</option>
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
              {{ carne.tipo }}
            </option>
          </select>
        </div>

        <div id="opcionais-container" class="input-container">
          <label id="opcionais-title" for="opcionais">Escolha os Opcionais</label>

          <div class="checkbox-container" v-for="opcional in opcionaisData" :key="opcional.id">
            <input
              type="checkbox"
              name="opcionais"
              id="opcionais"
              :value="opcional.tipo"
              v-model="opcionais"
            />
            <span>
              {{ opcional.tipo }}
            </span>
          </div>

          <div class="input-container">
            <input type="submit" class="submit-btn" value="Criar Meu Burger">
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from './Message.vue';

export default {
  name: "BurgerForm",
  components: {
    Message
  },
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisData: null,
      name: null,
      pao: null,
      carne: null,
      opcionais: [],
      msg: null
    }
  },
  methods: {
    async getIngredientes() {

      const req = await fetch('http://localhost:3000/ingredientes');
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisData = data.opcionais;

    },
    async createBurger(e) {
      e.preventDefault();
      
      const data = {
        name: this.name,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado",
      };

      const dataJson = JSON.stringify(data);

      const req = await fetch('http://localhost:3000/burgers', {
        method: "POST",
        headers: { 'Content-Type': 'application/json' },
        body: dataJson
      });

      const res = await req.json();

      // Colocar msg do sistema
      this.msg = `Pedido N° ${res.id} Realizado Com Sucesso!`;

      // Limpar msg do sistema
      setTimeout(() => this.msg = "", 3000);

      // Limpar os campos
      this.name = "";
      this.carne = "";
      this.pao = "";
      this.opcionais = [];
    }
  },
  mounted() {
    this.getIngredientes();
  }
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
  border-left: 4px solid #FCBA03;
}

input, select {
  padding: 5px 10px;
  width: 300px;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#opcionais-title {
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
  color: #FCBA03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: .3s;
}

.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>