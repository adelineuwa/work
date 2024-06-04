<template>
  <div class="container">
    <div class="holder">
      <div class="ad">
        <h1>BMI Calculator</h1>
        <div>
          <label for="weight">Weight (kg):</label>
          <input type="number" id="weight" v-model="weight">
        </div>
        <div>
          <label for="height">Height (m):</label>
          <input type="number" id="height" v-model="height">
        </div>
        <button @click="calculate">Calculate BMI</button>
        <p v-if="bmi">BMI is: {{ bmi }}</p>
        <p v-if="bmi">Weight : {{ weightCategory }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      weight: 0,
      height: 0,
      bmi: 0,
      weightCategory: "",
    };
  },
  computed: {
    mult() {
      return this.height > 0 && +this.weight > 0;
    },
  },
  methods: {
    calculate() {
      if (!this.mult) {
        return null;
      }
      this.bmi = this.weight / (this.height ** 2);
      this.weightCategory = this.result(this.bmi);
    },
    result(bmi) {
      if (bmi < 18.5) {
        return "Underweight";
      } else if (bmi < 24.9) {
        return "Normal weight";
      } else if (bmi < 29.9) {
        return "Overweight";
      } else {
        return "Obesity";
      }
    },
  },
};
</script>

<style>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.holder {
  display: flex;
  justify-content: center;;
  align-items: center;
  border: 1px solid red;
  background-color: rgb(10, 205, 226);
  height: 400px;
  width: 400px;
  border-radius: 20px;
}


h1{
  color: white;
  font-size: 50px;
  margin-bottom: none;
}


input{
  display: block;
  margin-bottom: 10px;
  justify-content: center;
  border: none;
  border-radius: 20px;
  padding: 10px;
  margin-left: 20px;
  text-align: center;
  width: 18rem;
  color: aliceblue;
  background-color: #000;
}

label{
  color: white;
  font-size: 35px;
  margin-bottom: none;
  display: flex;
  align-items: center;
  justify-content: center;
}

button{
 border-radius: 10px;
 padding: 10px;
 margin-left: 8em;
 border: none;
}
</style>
