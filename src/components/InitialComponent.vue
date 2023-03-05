<template>
<div class="container">
    <h1>Haz una pregunta</h1>

    <div class="mb-3">
      <input
        type="text"
        name="question"
        class="form-control"
        id="question"
        v-model="question"
      />
      
      <button 
      v-if="question"
      class="btn" 
      @click="handleNext"
      >
          Siguiente
      </button>

  </div>
</div>
</template>

<script>
import { ref } from "vue";

export default {

  emits:(["goto"]),

  setup(props, {emit}) {
    let question = ref(" ");
    let error = ref(" ");  

    let handleNext = () => {
       console.log("tigger")
          
          emit("goto", 1) 
      
    }

    return {
      question,
      error,
      emit,
      handleNext,
    };
  },
};
</script>

<style></style>
