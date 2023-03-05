<template>
  <!-- Componentes estáticos-->
  <!--<InitialComponent />
      <ConfirmComponent />
      <ResultsComponent />-->

  <!-- Componentes dinámicos -->
<div class="container">
<component
  :is="screens[position]"  
  @go-to="handleGoTo"
  /> <!--  Dependiendo del index = posición de la pantalla nos situaremos en una o en otra. -->
   <!-- @goto viene definido por el boton del children de InitialComponent -->
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
  let position = ref(0)

  let handleGoTo = (positions) => { /* Cogerá la posicion del array por eso se pasa como argumento */
    position = positions;
  }

  return {
    screens,
    position,
    handleGoTo
  }
}
}

</script>

<style>
@import "./assets/style.css";
</style>