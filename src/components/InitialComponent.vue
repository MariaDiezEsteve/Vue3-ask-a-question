<template>
<div>
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
      class="btn animate__animated animate__fadeIn" 
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
    const question = ref("");
    const error = ref(" ");  

    let handleNext = () => {
       // console.log("tigger")
          emit("goto", 1) 
          emit("question", question.value) 
      
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
