<template>
  <div class="calculadora-imc">
    <img alt="Calculadora" src="./calculadora.png">
    <h2>Calcular Índice de Massa Corporal</h2>
    <table align="center">
      <tr>
        <td> <label for="Peso">Peso (em Kg):</label> </td>
        <td> <input type="number" id="peso" v-model="peso"> </td>
      </tr>
      <tr>
        <td> <label for="Altura">Altura (em m):</label> </td>
        <td> <input type="number" id="peso" v-model="altura"> </td>
      </tr>
    </table> <br>
    <button @click="calcular">Calcular</button> <br>
    <div class="incompleto" v-if="incompleto"> <p>{{ incompleto }}</p> </div>
    <div class="resultado" v-if="resultado">
      <h3>Resultados</h3>
      <p>Seu IMC é: {{ resultado }}</p>
      <p>Sua categoria é: {{ categoria }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'calculadora-imc',
  data () {
       return {
        peso: null,
        altura: null,
        resultado: null,
        categoria:'',
        incompleto: ''
       };
  },
  methods: {
    calcular () {
      if (!this.peso || !this.altura) {
        this.incompleto="Você deve preencher todos os campos!";
        return
      }

      const imc = this.peso / (this.altura * this.altura);
      this.resultado = imc.toFixed(2);

      if (imc < 18.5) this.categoria = "Abaixo do peso";
      else if (imc < 24.9) this.categoria = "Peso normal";
      else if (imc < 29.9) this.categoria = "Excesso de peso";
      else if (imc < 34.9) this.categoria = "Obesidade classe I";
      else if (imc < 39.9) this.categoria = "Obesidade classe II";
      else if (imc >= 40.0) this.categoria = "Obesidade classe III";
    }
  }
}
</script>

<style scoped>
.calculadora-imc{
  background-color: rgb(213, 231, 236);
  max-width: 450px;
  margin: 0 auto;
  padding: 30px;
  border-radius: 10px;
}
.incompleto{
  color: red;
}
button{
  background-color: #084492;
  border: none;
  color: white;
  text-decoration: none;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
}
img{
  width: 100px;
  height: 100px;
}
h2, h3 {
  color: #084492;
}
h2{
  font-size: 28px;
}
h3{
  font-size: 24px;
}
p{
  font-size: 20px;
}
input{
  font-size: 20px;
  border-radius: 5px;
}
td {
  padding-top: 5px;
  padding-bottom: 5px;
  font-size: 22px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
