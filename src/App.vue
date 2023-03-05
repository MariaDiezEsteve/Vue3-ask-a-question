<template>

 
  <!-- Componentes estáticos-->
  <!--<InitialComponent />
      <ConfirmComponent />
      <ResultsComponent />-->

  <!-- Componentes dinámicos -->
  
  <div class="container">
    <transition name="fade" appear mode="out-in">
      <component
        :is="screens[position]"  
        :question="question" 
        :result="result"
        @goto="handleGoTo"
        @question="handleQuestion"
        @showResult ="showResult"
        /> <!--  Dependiendo del index = posición de la pantalla nos situaremos en una o en otra. -->
        <!-- @goto viene definido por el boton del children de InitialComponent -->
        <!-- question viene derterminado por el hijo InitialComponent.vue =>  emit("question", question.value)  -->
        <!-- :question="question" aquí estamos pasando al componente de ConfirmComponent como prop  -->
        <!-- :result="result" aquí estamos enviando los resultados al componente de ResultComponent como prop-->
      </transition>
  </div>
 
</template>

<script>
import InitialComponent from '@/components/InitialComponent.vue';
import ConfirmComponent from '@/components/ConfirmComponent.vue';
import ResultsComponent from '@/components/ResultsComponent.vue';

import {ref} from "vue"

export default{
components: {
  InitialComponent,
  ConfirmComponent,
  ResultsComponent
},
setup(){
  const screens = ["InitialComponent", "ConfirmComponent", " ResultsComponent"] /* Array con los diferentes componentes*/ 
  const position = ref(0)
  const question = ref("")
  const result = ref("")
  const list = [ "Si", "No", "Quizás", "No estoy segura, .. inténtalo de nuevo", "Pregunta a una amiga", "Tu madre que respondería", "Llama a la policía"]
  let rand = ref("")
  

  let handleGoTo = (positions) => { /* Cogerá la posicion del array por eso se pasa como argumento */
    position.value = positions;
  }

  let handleQuestion = (questions) => {
    question.value = questions
  }

  let getRandomValue = () => {
    return list[Math.floor(Math.random()* list.length)]
    
  }

  let generateResult = () =>{
     rand.value = getRandomValue

     result.value = rand.value
  }

  let showResult = () => {
    generateResult
  }

  return {
    screens,
    position,
    question,
    result, 
    list,
    rand,
    handleQuestion,
    handleGoTo,
    getRandomValue,
    generateResult,
    showResult
  }
}
}

</script>

<style>
@import "./assets/style.css";
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: 0.5s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: 0.5s;
}
.fade-leave-to {
  opacity: 0;
}
</style>