<template>
  <h1 :class=" classCounter ">{{counter}}</h1>
   <button @click='incrementar'>Incrementar</button>
   <button @click='decrementar'>Decrementar</button>
   <button @click='resetear'>Resetear</button>
   <button @click='agregar' :disabled="isNumero">Agregar</button>
   <br/>
   <div>{{ arr }}</div>
   <ul>
    <li v-for=" (num, index) in arr" :key="index"> {{ num }}</li>
   </ul>
</template>

<script  setup>
    import {computed, ref} from 'vue';
    const counter = ref(0);
    const arr = ref([]);

function incrementar(){
  counter.value++
}
function decrementar(){
  counter.value--
}
function resetear(){
  counter.value = 0
}

function agregar(){  
    arr.value.push(counter.value)   
}

const isNumero = computed(()=>{
  return arr.value.includes( counter.value)
})
  
  
const classCounter = computed(()=>{
  if( counter.value === 0){
    return 'zero'
  }
  if( counter.value < 0 ){
    return 'negativo'
  }
  if( counter.value > 0 ){
    return 'positivo'
  }

})
</script>

<style scoped>
 
  .positivo {
    color: green;
  }
  .negativo {
    color: red;
  }
  .zero{
    color: navy;
  }
</style>