<template>
  <div class="container text-center">
    <h1 :class=" classCounter ">{{counter}}</h1>
   <button class="btn btn-primary" @click='incrementar'>Incrementar</button>
   <button class="btn btn-danger" @click='decrementar'>Decrementar</button>
   <button class="btn btn-secondary" @click='resetear'>Resetear</button>
   <button class="btn btn-warning" @click='agregar' :disabled="isNumero">Agregar</button>
   <!--
    <br/>
   <div>{{ arr }}</div>
   -->  
   <ul class="list-group">
    <li class="list-group-item" v-for=" (num, index) in arr" :key="index"> {{ num }}</li>
   </ul>
  </div>  
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