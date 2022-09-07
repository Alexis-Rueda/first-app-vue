<script setup>
import { ref, computed } from 'vue';
const name = 'Vue dinámico';
// const styleColor = 'color: blue';
// const arrayColores = ['blue', 'red', 'peru'];
// const activo = true;
// const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
// const arrayFrutas = [
//         {
//             name: "Manzana",
//             price: "$1.00",
//             description: "Una manzana",
//             id: 1,
//         },
//         {
//             name: "Pera",
//             price: "$2.00",
//             description: "Una pera",
//             id: 2,
//         },
//         {
//             name: "Naranja",
//             price: "$3.00",
//             description: "Una naranja",
//             id: 3,
//         },
//     ];
// const objetoFruta = {
//             name: "Manzana",
//             price: "$1.00",
//             description: "Una manzana",
//             id: 1,
//         };
// const arrayFrutas = [
// {
// name: "Manzana",
// price: "$1.00",
// description: "Una manzana",
// stock: 0,
// },
// {
// name: "Pera",
// price: "$2.00",
// description: "Una pera",
// stock: 10,
// },
// {
// name: "Naranja",
// price: "$3.00",
// description: "Una naranja",
// stock: 20,
// },
// ];

//metodo -methods
// const handleClick = (message) => {
//   console.log(message);
// }

const counter = ref(0);

const increment = () => counter.value++;

const decrement = () => counter.value--;

const reset = () => counter.value = 0;

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  };
  if (counter.value > 0) {
    return 'positive'
  };
  if (counter.value < 0) {
    return 'negative'
  };
});

const arrayFavoritos = ref([]);

const add = () => {
  arrayFavoritos.value.push(counter.value);
};

const bloquerBtnAdd = computed(() => {
  // if(arrayFavoritos.value.includes(counter.value)){
  //   return true;
  // } else {
  //   return false
  // };
  const numSearch = arrayFavoritos.value.find((num) => num === counter.value);
  // if (numSearch === 0) return true;
  // return numSearch ? true: false;
  return numSearch || numSearch === 0;
});


</script>

<template>
  <!-- <h1>Hola {{ name.toUpperCase() }}</h1> -->
  <!-- <h2>{{ arrayColores }}</h2>
  <h2 :style="`color: ${arrayColores[2]}`" >Soy peru</h2>
  <h2>{{ activo ? 'Estoy activo' : 'Estoy inactivo' }}</h2>
  <h2 v-if="activo === true" >Estoy activo</h2>
  <p v-else-if="activo === false" >Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>

  <h2 v-show="activo">Estoy activo v-show</h2> -->
  <!-- <ul> -->
  <!-- <li v-for="(fruta, index) in arrayFrutas" :key="index " >
      {{index}} - {{ fruta }}
    </li> -->
  <!-- <li v-for="fruta in arrayFrutas" :key="fruta.id" >
      {{fruta.name}} - {{fruta.price}} - {{fruta.description}}
    </li> -->
  <!-- <li v-for="(value, propiedad, index) in objetoFruta" :key="value">
      {{index}} - {{propiedad}} : {{value}}
    </li> -->
  <!-- <template v-for="item in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0">{{ item.name }} - {{ item.price }}</li>
    </template> -->
  <!-- </ul> -->
  <!-- <button v-on:click.right.prevent="handleClick('Texto Rigth')" >Activame right</button>
  <button @click="handleClick('Texto Left')" >Activame left</button>
  <button @click.middle="handleClick('Texto Middle')" >Activame middle</button> -->

  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <!-- <h2 :style="`color: ${counter < 0 ? 'red' : counter > 0 ? 'green': 'black' }`">{{counter}}</h2>
    <h2 v-if="counter < 0" :style="'color: red'">{{ counter }}</h2>
    <h2 v-else-if="counter > 0" :style="'color: green'">{{ counter }}</h2>
    <h2 v-else>{{ counter }}</h2>
    <h2 :class="counter > 0 ? 'positive' : 'negative'">{{ counter }}</h2> -->
    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success" >Increment</button>
      <button @click="decrement" class="btn btn-danger">Decrement</button>
      <button @click="reset" class="btn btn-secondary" >Reset</button>
      <button @click="add" :disabled="bloquerBtnAdd" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(num, index) in arrayFavoritos" :key="index">{{ num }}</li>
    </ul>
  </div>
</template>


<style>
h1 {
  color: red;
}

.positive {
  color: green;
}

.negative {
  color: red;
}

.zero {
  color: peru;
}
</style>