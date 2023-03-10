<script setup>
import {defineProps,ref,provide} from 'vue';
import Question from './question.vue'
import Option from './option.vue'
const {quiz} = defineProps(['quiz'])
const random = ref([])
const newnum = ref(null);
const currentQuestion = ref(0)
const i = ref(0)
const iscorrect = ref('btn-secondary')
const option_id  = ref(false)
const completed = ref(false)
const score =ref(0)
const scoreInfo =[]


const randoomQuestions =(max) =>{
for(i.value=1;i.value<=max;i.value++){
 newnum.value =  Math.floor(Math.random() * (max));
 while (random.value.includes(newnum.value)){
  newnum.value =  Math.floor(Math.random() * (max));
 }
 random.value.push(newnum.value);
}
}
randoomQuestions(quiz.questions.length)
const  option_selected = (option__id)=>{
    option_id.value = option__id
    if(option__id == quiz.questions[random.value[currentQuestion.value]].correct){
        iscorrect.value = 'btn-success'
        score.value++
    }
    else {
        iscorrect.value = 'btn-danger'
        scoreInfo.push({'question_id':quiz.questions[random.value[currentQuestion.value]].id})
    }

}
const nextQuestion = ()=>{
    if(option_id.value!=false){
        if(currentQuestion.value < quiz.questions.length-1){
    currentQuestion.value++
    iscorrect.value = 'btn-secondary'
    option_id.value=false
    }
    else{
        completed.value = true
    }
    }
   
    
}
</script>
<template>
     <div class="d-flex justify-content-center row">
            <div class="col-md-10 col-lg-10">
                <div class="border">
                    <div class="question bg-white p-3 border-bottom">
                        <div class="d-flex flex-row justify-content-between align-items-center mcq">
                            <h4 style="color:rgb(8, 152, 119);">{{ quiz.name }}</h4><span>({{ currentQuestion }} of {{ quiz.questions.length }})</span></div>
                    </div>
                    <div class="question bg-white p-3 border-bottom">
                        <div class="d-flex flex-row align-items-center question-title">
                           <Question :question="quiz.questions[random[currentQuestion]]"/>
                        </div>
                        <div class=" row justify-content-between">
                            <Option v-for="option in quiz.questions[random[currentQuestion]].options" :key="option.id" :option="option" @selected-option="option_selected" :iscorrect="iscorrect" :selected_option_id ="option_id" ></Option>
                        </div>
                        </div>
                    <div class="d-flex flex-row justify-content-between align-items-center p-3 bg-white"><button @click="$emit('return-home')" class="btn btn-primary d-flex align-items-center btn-danger" type="button"><i class="fa fa-angle-left mt-1 mr-1"></i>&nbsp;Exit</button>
                        <button  v-if="completed" class="btn btn-primary border-success align-items-center btn-success" type="button" @click="$emit('return-result',{'score':score,'info':scoreInfo})">View Result<i class="fa fa-angle-right ml-2"></i></button>
                        <button  v-if="!completed" class="btn btn-primary border-success align-items-center btn-success" type="button" @click="nextQuestion" :disabled="!option_id">Next<i class="fa fa-angle-right ml-2" ></i></button></div>
                </div>
            </div>
        </div>
</template>
<style scoped>
</style>

