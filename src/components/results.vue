<script setup>
import {defineProps,ref} from 'vue';
const {result} = defineProps(['result'])
const answers = ref([])
for (const question of result.quiz.questions){
    for(const question1 of result.Info.info){
        if(question.id==question1.question_id){
            answers.value.push(question)
        }
    }
}
</script>

<template>
   

    <div class=" text-center mt-4">
            <h3 style="color:rgb(8, 152, 119);">
                {{result.quiz.name}}
            </h3> 
            <h5>Your score is  ({{result.Info.score}}/{{result.quiz.questions.length}})</h5>
        </div>
       

       <ul class="fs-5 mt-5 p-2" style="width:70%;margin: auto;">
    
            <ol class="list-group list-group"  v-for="question in answers" :key="question.id">
                <li class="list-group-item d-flex justify-content-between align-items-start">
                    <div class="ms-2 me-auto">
                    <div class="fw-bold"> Question : {{ question.text }}</div>
                    Answer : {{ question.answer }}
                    </div>
                </li>
            </ol>
      
       
       </ul>
       <div class=" text-center mt-4">
        <button  @click="$emit('return-home')" type="button" class="btn btn-warning">Return</button>
        <button @click="$emit('start-quiz')" type="button" class="btn btn-success ms-3">Re Start</button>
        </div>
</template>

<style>


</style>