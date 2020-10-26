<template>
  <div class="calculadora">
    <div class="resultado">{{ resultado }}</div>
    <button data-opcion="clear" class="btn oscuro" @click="limpiar">C</button>
    <button class="btn oscuro" @click="realizarOperacion('/')">/</button>
    <button class="btn oscuro" @click="realizarOperacion('*')">*</button>
    <button class="btn oscuro" @click="realizarOperacion('-')">-</button>
    <button class="btn" @click="imprimirNumero(7)">7</button>
    <button class="btn" @click="imprimirNumero(8)">8</button>
    <button class="btn" @click="imprimirNumero(9)">9</button>
    <button class="btn oscuro add" @click="realizarOperacion('+')">+</button>
    <button class="btn" @click="imprimirNumero(4)">4</button>
    <button class="btn" @click="imprimirNumero(5)">5</button>
    <button class="btn" @click="imprimirNumero(6)">6</button>
    <button class="btn" @click="imprimirNumero(1)">1</button>
    <button class="btn" @click="imprimirNumero(2)">2</button>
    <button class="btn" @click="imprimirNumero(3)">3</button>
    <button
      data-opcion="igualar"
      class="btn oscuro equals"
      @click="obtenerResultado"
    >
      =
    </button>
    <button class="btn cero" @click="imprimirNumero(0)">0</button>
    <button id="btnPunto" class="btn" @click="imprimirNumero('.')">.</button>
  </div>
</template>

<script>
export default {
  name: "Calculadora",
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacion: "",
      estadoInicial: true,
      resultado: 0,
    }
  },
  methods: {
    toggleOperaciones(estado) {

      if (estado == "activar") {
        document.getElementsByClassName('oscuro').item(1).removeAttribute('disabled');
        document.getElementsByClassName('oscuro').item(2).removeAttribute('disabled');
        document.getElementsByClassName('oscuro').item(3).removeAttribute('disabled');
        document.getElementsByClassName('oscuro').item(4).removeAttribute('disabled');
      } else {
        document.getElementsByClassName('oscuro').item(1).setAttribute('disabled', 'disabled');
        document.getElementsByClassName('oscuro').item(2).setAttribute('disabled', 'disabled');
        document.getElementsByClassName('oscuro').item(3).setAttribute('disabled', 'disabled');
        document.getElementsByClassName('oscuro').item(4).setAttribute('disabled', 'disabled');
      }
    },
    limpiar() {
      this.numero1 = 0;
      this.numero2 = 0;
      this.operacion = "";
      this.estadoInicial = true;
      this.resultado = 0;
      document.getElementById("btnPunto").removeAttribute("disabled");
      this.toggleOperaciones("activar");

    },
    imprimirNumero(numero) {

      if (numero == ".") {
        document.getElementById("btnPunto").setAttribute('disabled', 'disabled')
      }

      if (this.estadoInicial == true) {
        this.estadoInicial = !this.estadoInicial;
        this.resultado = "";
        this.resultado += numero;
      } else {
        this.resultado += numero;
      }
    },
    realizarOperacion(op) {
      switch (op) {
        case '+':
          this.numero1 = parseFloat(this.resultado);
          this.resultado = "";
          this.operacion = "+";
          document.getElementById("btnPunto").removeAttribute("disabled");
          this.toggleOperaciones("desactivar");
          break;
        case '-':
          this.numero1 = parseFloat(this.resultado);
          this.resultado = "";
          this.operacion = "-";
          document.getElementById("btnPunto").removeAttribute("disabled");
          this.toggleOperaciones("desactivar");
          break;
        case '*':
          this.numero1 = parseFloat(this.resultado);
          this.resultado = "";
          this.operacion = "*";
          document.getElementById("btnPunto").removeAttribute("disabled");
          this.toggleOperaciones("desactivar");
          break;
        case '/':
          this.numero1 = parseFloat(this.resultado);
          this.resultado = "";
          this.operacion = "/";
          document.getElementById("btnPunto").removeAttribute("disabled");
          this.toggleOperaciones("desactivar");
          break;

        default:
          break;
      }
    },
    obtenerResultado() {
      switch (this.operacion) {
        case '+':
          this.numero2 = parseFloat(this.resultado);
          this.resultado = "";
          this.resultado = this.numero1 + this.numero2;
          break;
        case '-':
          this.numero2 = parseFloat(this.resultado);
          this.resultado = "";
          this.resultado = this.numero1 - this.numero2;
          break;
        case '*':
          this.numero2 = parseFloat(this.resultado);
          this.resultado = "";
          this.resultado = this.numero1 * this.numero2;
          break;
        case '/':
          this.numero2 = parseFloat(this.resultado);
          this.resultado = "";
          if ((this.numero1 / this.numero2) == "Infinity") {
            alert("No se puede dividir entre cero");
            this.limpiar();
          } else {
            this.resultado = this.numero1 / this.numero2;
          }
          break;

        default:
          this.resultado = "Error";
          break;
      }
      this.numero1 = 0;
      this.numero2 = 0;
      this.operacion = "";
      this.estadoInicial = true;
      document.getElementById("btnPunto").removeAttribute("disabled");
      this.toggleOperaciones("activar");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculadora {
  background-color: rgba(162, 199, 255, 0.4);
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(5, 1fr);
  border-radius: 5px;
}
.resultado {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 5px;
  color: whitesmoke;
  text-align: end;
  padding: 10px;
  max-height: 40px;
  font-size: 2em;
  grid-column: span 4;
  grid-row: 1;
}
.btn {
  padding: 25px;
  cursor: pointer;
  border: none;
  outline: none;
  margin: 3px;
  font-weight: bold;
  font-size: 1.5em;
}
.oscuro {
  background-color: rgba(163, 163, 163, 0.5);
}
.btn:hover {
  background-color: rgba(239, 239, 239, 0.9);
}
.oscuro:hover {
  background-color: rgba(163, 163, 163, 0.7);
}
.add,
.equals {
  grid-row: span 2;
}
.cero {
  grid-column: span 2;
}
</style>
