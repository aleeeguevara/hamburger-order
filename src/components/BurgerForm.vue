<template>
  <div>
    <p>Message Component</p>
    <div>
      <form id="burger-form">
          <label for="name" class="input-container">Client Name:
            <input type="text" id="name" name="name" v-model="name" placeholder="Type your name">
          </label>
          <label for="bun" class="input-container"> Choose bun:
            <select name="bun" id="bun" v-model="bun">
              <option value="">Select your bun</option>
              <option value="wholemeal">Wholemeal</option>
            </select>
          </label>
          <label for="meat" class="input-container"> Choose Meat:
            <select name="meat" id="meat" v-model="meat">
              <option value="">Select your meat</option>
              <option value="maminha">Maminha</option>
            </select>
          </label>
          <div class="input-container" >
            <label for="optionals" id="optionals-container"> Choose optionals:
            <div class="checkbox-container">
              <input type="checkbox" name="optionals" v-model="optional" value="Salami">
              <span>Salami</span>
            </div>
            </label>
          </div>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Create my Burger!">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BurgerForm',
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
    padding: 5px 310px;
    margin-top: 15px;
    width: 300px;
  }

  #optionals-container {
    flex-direction: row;
    flex-wrap: wrap;
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
    margin-left: 6px;
    margin-top: 15px;
    font-weight: bold;
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
