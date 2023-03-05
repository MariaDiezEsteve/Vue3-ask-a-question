<template>
  <div>
    <h3>Tu respuesta es: </h3>
    <div class="viewer"> {{ result }}</div> <!-- Aquí estamos pasando la pregunta como props del padre al hijo para que se visualice en este componente  -->

    <div class="animate__animated animate__bounceIn animate__delay-1s">
      <hr>
      <button 
      class="btn"
      @click="starOver">
        Volver a empezar
      </button>
      <button 
      class="btn"
      @click="getResult"
      >
       Decide otra vez
      </button>
    </div>

  </div>
</template>

<script>
import {onMounted} from 'vue';

export default {
  
  props: {
    result: String,
  },
 
  setup(props, {emit}){

    onMounted(() => {
      getResult
     })

    const starOver= () => {

    }
    const getResult= () => {
      emit("showResult");
    }

    return {
      starOver,
      getResult, 
      onMounted
    }
  }

}
</script>

<style>

</style>