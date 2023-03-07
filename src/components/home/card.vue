<script setup>
import { defineProps } from 'vue';
const {quiz} = defineProps(['quiz'])


</script>
<template>
    <div  class="col-3 card mt-5 p-0" style="width: 14rem;cursor: pointer;">
          <img :src="quiz.img" class="card-img-top " alt="...">
          <div class="card-body">
            <p class="card-text fs-4">{{quiz.name}}</p>
            <p class="card-text fs-6">{{quiz.questions.length}} questions</p>
          </div>
     </div>
</template>

<style>
</style>