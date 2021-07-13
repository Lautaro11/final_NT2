<template>
  <div class="final">
    <h4><u>Input</u></h4>
    <input type="text" :value="input" @input="actualizar($event)" /> <br />
    <br />
    <h4>cantidad: {{ input.length }}</h4>
    <br />
    <h4>{{ input1 | codificar }} (Codificado)</h4>
    <br />
    <h4>{{ input2 | mayuscula }} (Mayúscula)</h4>
    <br />
    <h4>{{ input3 | minuscula }} (Minúscula)</h4>
    <br />
    <h4>{{ input4 | mix1 }} (Mayúsculas y minúsculas)</h4>
    <br />
    <h4>{{ input5 | mix2 }} (Minúsculas y mayúsculas)</h4>

    <br><hr>
    <p>Respuestas: 1:b, 2:b , 3:c, 4:b, 5:b,c </p>
    
  </div>
</template>

<script>
export default {
  name: "Codificacion",
  data() {
    return {
      input: "",
      input1: "",
      input2: "",
      input3: "",
      input4: "",
    };
  },
  methods: {
    actualizar(e) {
      let ing = e.target.value;
      this.input = ing;
      this.input1 = ing;
      this.input2 = ing;
      this.input3 = ing;
      this.input4 = ing;
      this.input5 = ing;
    },
  },
  computed: {},
  filters: {
    codificar: function(value) {
      let palabraCodificada = '';
      let palabraMinuscula = value.toLowerCase();
      for (let i = 0; i < String(value).length; i++) {
        let letra = palabraMinuscula[i];
        switch (letra) {
          case "a":
            letra = "u"
            break;
          case "e":
            letra = "o"
            break;
          case "o":
            letra = "e"
            break;
          case "u":
            letra = "a"
            break;
        }
        palabraCodificada += letra;
      }
      return palabraCodificada;
    },
    mayuscula: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.toUpperCase();
    },
    minuscula: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.toLowerCase();
    },
    mix1: function (value) {
      value = String(value);
      var flip = '';
      for (var i = 0; i < String(value).length; i++) {
        if(i % 2 === 0){
          flip += value.charAt(i).toUpperCase();
        } else {
          flip += value.charAt(i).toLowerCase();
        }
      }
      return flip;
    },
    mix2: function (value) {
      value = String(value);
      var flip = '';
      for (var i = 0; i < String(value).length; i++) {
        if(i % 2 !== 0){
          flip += value.charAt(i).toUpperCase();
        } else {
          flip += value.charAt(i).toLowerCase();
        }
      }
      return flip;
    },
    
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
