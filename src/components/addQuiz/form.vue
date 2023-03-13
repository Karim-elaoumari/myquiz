<script setup>
import {ref,inject} from 'vue'
import axios from "axios";
const quizes1 = inject('quizes')
const quizes = ref(quizes1)

const quizValue = ref({ 
     id: quizes.length+1,
     img: '',
     name: '',
     questions:[]
});
const questionsCount  = ref(0)
quizValue.value.questions.push({ 
                 id: questionsCount.value+1,
                 text: '',
                 correct :'',
                 answer :"",
                 options:[{
                    id:1,
                    text :''
                    }
                ]
                })
const submit = () => {
  // Add the quiz to the server
  axios.post('https://myquiz-server.herokuapp.com/quizes', quizValue.value)
    .then((response) => {
      // If the POST request was successful, add the new quiz to the local quizes array as well
      
    })
    .catch((error) => {
      console.error(error)
    })
}

const addQuestion = ()=>{
    questionsCount.value++
    quizValue.value.questions.push({ 
                 id: questionsCount.value+1,
                 text: '',
                 correct :'',
                 answer :"",
                 options:[{
                    id:1,
                    text :''
                    }
                ]
        })
   
}
const addOption = (index)=>{
    quizValue.value.questions[index].options.push({
                        id: quizValue.value.questions[index].options.length+1,
                        text: ''})
}
</script>

<template>
<div class="container">
  <h2 style="color: rgb(8, 152, 119);">Add a New Quiz</h2>
  <div>
    <div class="form-group">
      <label >Quiz Name:</label>
      <input type="text" class="form-control" v-model="quizValue.name" required><br>
      <label >Quiz Image:</label>
      <input type="text" class="form-control" placeholder="place the url of the image here" v-model="quizValue.img"  required>
    </div>
    <hr>
    <div id="questions">
        <h3 style="color: rgb(8, 152, 119);">Questions:</h3>
        <div class="question" v-for="(question, index) in quizValue.questions" :key="index">
        <div class="form-group">
          <label class="fs-5" style="color:blue;">Question {{ index+1 }}:</label> <br>
          <label class="fs-6">question name : </label>
          <input type="text" class="form-control" v-model="question.text">
          <label class="fs-6">question answer : </label>
          <input type="text" class="form-control" v-model="question.answer">
        </div>
            <div class="answer-group" v-for="(option, optionIndex) in question.options" :key="optionIndex">
                <div class="form-group">
                    <label for="answer1-1" style="color:brown">Option {{ optionIndex+1 }}:</label>
                    <input type="text" class="form-control" v-model="option.text" >
                    <div class="form-check">
                    <input class="form-check-input correct-answer" :value="optionIndex+1" type="radio" v-model="question.correct">
                    <label class="form-check-label" for="correct-answer1-1">
                        Correct answer
                    </label>
                    </div>
                </div>
            </div>
       
        <button type="button" class="btn btn-secondary add-answer" @click="addOption(index)">Add Option</button>
      </div>
      <hr>
    </div>
  
    <button type="button" class="btn btn-primary" @click="addQuestion" > Add Question</button>
    <hr>
    <button type="button" class="btn btn-success" @click="submit">Submit Quiz</button>
    <button type="button" class="btn btn-warning" @click="$emit('return-home')">Return home</button>
</div>
</div> 

</template>
<script scope>
</script>