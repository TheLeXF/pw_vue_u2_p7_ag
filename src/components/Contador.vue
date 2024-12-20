<template>
  <h2>{{ encabezado }} : {{valor2}}</h2>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <div>
    <button @:click="incrementar()">+1</button>
    <button v-on:click="decremetar()">-1</button>
  </div>

  <div v-if="esVerdad">
    <h1>Feliz Año nuevo</h1>
  </div>


</template>

<script>
export default {
  data() {
    return {
      numero: this.valor,
      titulo: "Contador",
    };
  },
  methods: {
    calcularCuadrado() {
      console.log("Entro a calcular");
      return this.numero * this.numero;
    },
    incrementar() {
      this.numero++;
    },
    decremetar() {
      this.numero--;
    },

  },
  computed: {
    calcularCuadradoComputado() {
      console.log("Entro a calcular computado");
      return this.numero * this.numero;
    },
  },
  //Primera forma de declarar un props
  //props:['encabezado','valor']

  props:{
    encabezado:{
      type:String,
      required:false,
      default:"Hola mundo",
      validator(value){
        return value.includes('j')
      }
    },
    valor:Number,
    valor2:{
      type:Number,
      required:false,
      default:77,
      validator(value){
        //programo mi validacion bajo mi criterio y retorno true 
        //cuando es valido para mi 
        //retorno false cuando no es valido para mi
        return value<=77;
      }
    },
    esVerdad:{
      type:Boolean,
      required:true
    },
    arreglo:Array ,
    fecha:Date,
    objetoPersona:Object
  },
};
</script>

<style>
button {
  background: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  margin: 0px 5px;
  padding: 5px 15px;
}

button:hover {
  background: #5aa67b;
}
</style>
