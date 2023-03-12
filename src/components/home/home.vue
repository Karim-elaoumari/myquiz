<script setup>
import {ref,watch,inject} from 'vue';
import Card from './card.vue'
const quizes1 = inject('quizes')
const quizes = ref(quizes1)
const search = ref("")
 watch(search,() =>{
  quizes.value = quizes1.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
 });
</script>
<template>
        <div class=" text-center">
            <h3 style="color:rgb(8, 152, 119);">
                Pick A Quiz 
            </h3> 
        </div>
       <div class="row mt-2">
         <div class="col-8">
            <input class=" form-control" v-model="search" type="search" placeholder="Search Quiz ..." >
         </div>
         <div class="col">
            <button @click="$emit('add-quiz')" type="button" class=" btn btn-success">Add Quiz</button>
         </div>

        </div>
        <div class="row p-2 justify-content-between">
        <Card  @click="$emit('quiz-selected', quiz)" v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" style="margin:auto;"/>


        </div>
        
</template>
<style scoped>
.form-control:focus {
    box-shadow: none;
    border-color: rgb(8, 152, 70);
    border-width: 2.5px;
}
.form-control{
    box-shadow: none;
    border-color: rgb(8, 152, 119);
    border-width: 2px;
}
</style>