<template>
  <div class="card">
    <h2>{{ fromCurrency }} em {{ toCurrency }}</h2>
    <input
      type="text"
      v-model="currency_value"
      v-bind:placeholder="fromCurrency"
    />
    <button class="btn" v-on:click="convertCurrency()">Converter</button>
    <h2>{{ convert_value }}</h2>
  </div>
</template>

<script>
export default {
  name: "Convert",
  props: ["fromCurrency", "toCurrency"],
  data() {
    return {
      currency_value: "",
      convert_value: 0,
    };
  },
  methods: {
    convertCurrency() {
      let q = this.fromCurrency + "_" + this.toCurrency;
      let apiKey = "1db78cbc0880dd40a474";
      let _url =
        "https://free.currconv.com/api/v7/convert?q=" +
        q +
        "&compact=ultra&apiKey=" +
        apiKey;

      console.log(q);
      console.log(_url);

      fetch(_url)
        .then((response) => {
          return response.json();
        })
        .then((json) => {
          let price = json[q];
          this.convert_value = price * parseFloat(this.currency_value);
        });
    },
  },
};
</script>

<style scoped>
.card {
  padding: 1rem;
  width: 360px;
  border-radius: 25px;
  box-shadow: 4px 5px 4px rgba(0, 0, 0, 0.25);
  background-color: chocolate;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  gap: 10px;
  align-items: center;
}
input {
    border-radius: 25px;
    padding: 10px;
    width: 80%;
    border: 1px solid chocolate;
}

input:focus {
    outline: 0;
    border: 2px solid chocolate; 
}

.btn {
    border-radius: 25px;
    box-shadow: 4px 5px 4px rgba(0, 0, 0, 0.20);
    background-color: #fff;
    padding: 8px 16px;
    border: none;
    width: 150px;
}
</style>