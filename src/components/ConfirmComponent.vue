<template>
  <div>
    <h3>Tu pregunta es: </h3>
    <div class="viewer"> {{ question }}</div> <!-- Aquí estamos pasando la pregunta como props del padre al hijo para que se visualice en este componente  -->

    <div class="animate__animated animate__bounceIn animate__delay-1s">
      <hr>
      <button 
      class="btn"
      @click="goNext">
        Pregunta correcta
      </button>
      <button 
      class="btn"
      @click="goBack"
      >
        Volver a hacer la pregunta
      </button>
    </div>

  </div>
</template>

<script>

export default {
  props: {
    question: String,
  },
  setup(props, {emit}){
    let goNext = () => {
      emit("goto", 2) 
    }
    let goBack = () => {
      emit("goto", 0) 
      emit("question", " ") // Al regresar a la página de InitialComponent aquí le estamos diciendo que elimine la pregunta para realizar otra. Estamos limpiando el estado.
    }

    return{
      goNext,
      goBack
    }
  }
}

</script>

<style>

</style>