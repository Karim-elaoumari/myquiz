<script setup>
import {ref,provide} from 'vue'
import q from './data/quizes.json'
import Quiz from './components/quiz/index.vue'
import Home from './components/home/home.vue'
import Stepper from './components/stepper.vue'
import Instractions from './components/instractions.vue'
import Results from './components/results.vue'


const quizSelected = ref(null)
const currentComponent = ref(Home)
const currentStep = ref(1)
const selectedQuiz = (newquizSelected)=>{
  currentStep.value = 2 
  currentComponent.value = Instractions
  quizSelected.value=newquizSelected
}
const startQuiz = ()=>{
  currentStep.value = 3 
  currentComponent.value = Quiz
}
const returnHome  = ()=>{
  currentStep.value = 1
  currentComponent.value = Home
}
const showResult = ()=>{
  currentStep.value = 4
  currentComponent.value = Results
}
provide('quizes', q)
</script>
<template>
  <header>
    <div class="row">
          <div class="col-xs-12 col-md-8 offset-md-2 block border" >
            <Stepper :currentStep="currentStep"/>
          </div>
    </div>
  </header>
  <main class="">
    <div class="row ">
      <div class="col-xs-12 col-md-8 offset-md-2 block border" style="min-height: 70vh;">
        <component :is="currentComponent"  @quiz-selected="selectedQuiz" :quiz="quizSelected" @start-quiz="startQuiz" @return-home="returnHome" @return-result="showResult"/>
      </div>
   </div>
  </main>
  <!-- HTML !-->



</template>
<style scoped>


</style>
