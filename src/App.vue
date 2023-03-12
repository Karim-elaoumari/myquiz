<script setup>
import axios from "axios";
import {ref,provide} from 'vue'
import Quiz from './components/quiz/index.vue'
import Home from './components/home/home.vue'
import Stepper from './components/stepper.vue'
import Instractions from './components/instractions.vue'
import Results from './components/results.vue'
import AddQuiz from './components/addQuiz/form.vue'

const q = null
const fetchQuizes = () => {
      axios
        .get("https://myquiz-server.vercel.app/api/quizes")
        .then((response) => {
          q= response.data;
        });
};
fetchQuizes()
const quizSelected = ref(null)
const currentComponent = ref(Home)
const currentStep = ref(1)
const resultOfQuizz =ref(null)
const selectedQuiz = (newquizSelected)=>{
  currentStep.value = 2 
  currentComponent.value = Instractions
  quizSelected.value=newquizSelected
}
const startQuiz = ()=>{
  currentStep.value = 3 
  currentComponent.value = Quiz
}
const returnHome = ()=>{
  currentStep.value = 1
  currentComponent.value = Home
}
const showResult = (resultOfQuiz)=>{
  resultOfQuizz.value = {'quiz':quizSelected,'Info':resultOfQuiz}
  currentStep.value = 4
  currentComponent.value = Results
}

const add_Quiz = ()=>{
  currentComponent.value = AddQuiz
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
        <component :is="currentComponent"  @quiz-selected="selectedQuiz" :quiz="quizSelected"  @start-quiz="startQuiz" @return-home="returnHome" @return-result="showResult"  @add-quiz="add_Quiz" :result="resultOfQuizz"/>
      </div>
   </div>
  </main>
  <!-- HTML !-->



</template>
<style scoped>


</style>
