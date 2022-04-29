<template>
  <div>
    <MessageComponent :msg="msg" v-show="msg"/>
    <div>
      <form id="burger-form" @submit="createBurger">
          <label for="name" class="input-container">Client Name:
            <input type="text" id="name" name="name" v-model="name" placeholder="Type your name">
          </label>
          <label for="bun" class="input-container"> Choose bun:
            <select name="bun" id="bun" v-model="bun">
              <option value="">Select your bun</option>
              <option v-for="bun in buns" :key="bun.id" :value="bun.tipo">{{bun.tipo}}</option>
            </select>
          </label>
          <label for="meat" class="input-container"> Choose Meat:
            <select name="meat" id="meat" v-model="meat">
              <option value="">Select your meat</option>
              <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">{{meat.tipo}}</option>
            </select>
          </label>
          <label for="optionals" id="optionals-container"> Choose optionals:
            <div class="input-container">
              <div class="checkbox-container" v-for="optional in optionalsdata" :key="optional.id" >
                <input type="checkbox" name="optionals" v-model="optionals" :value="optional.tipo">
                <span>{{optional.tipo}}</span>
              </div>
            </div>
          </label>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Create my Burger!">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import MessageComponent from './Message.vue';

export default {
  name: 'BurgerForm',
  data() {
    return {
      name: null,
      buns: null,
      meats: null,
      optionalsdata: null,
      bun: null,
      meat: null,
      optionals: [],
      msg: null,
    };
  },
  methods: {
    async getIngridients() {
      const req = await fetch('http://localhost:3000/ingredientes');
      const data = await req.json();

      this.buns = data.paes;
      this.meats = data.carnes;
      this.optionalsdata = data.opcionais;
    },
    async createBurger(e) {
      e.preventDefault();
      const data = {
        nome: this.name,
        pao: this.bun,
        carne: this.meat,
        opcionais: Array.from(this.optionals),
        status: 'Solicitado',
      };

      const dataJson = JSON.stringify(data);

      const req = await fetch('http://localhost:3000/burgers', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: dataJson,
      });

      const res = await req.json();
      this.msg = `Your order n° ${res.id} has been received!`;

      setTimeout(() => { this.msg = null; }, 3000);

      this.name = '';
      this.bun = '';
      this.meat = '';
      this.optionals = '';
    },
  },
  mounted() {
    this.getIngridients();
  },
  components: {
    MessageComponent,
  },
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
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
  }

  input, select {
    padding: 5px 10px;
    margin-top: 15px;
    width: 400px;
  }

  .input-container{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }

  .checkbox-container {
    width: 50%;
    display: flex;
  }

  .checkbox-container span,
  .checkbox-container input {
    margin-left: 6px;
    margin-top: 15px;
    font-weight: bold;
  }
  .checkbox-container input {
    width: 10px;
  }

  .submit-btn {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
    transition: .5s;
  }

  .submit-btn:hover {
    background-color: transparent;
    color: #222;
  }
</style>
