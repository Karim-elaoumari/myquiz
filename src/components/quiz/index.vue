<script setup>
import {defineProps,ref} from 'vue';
import Loader from './loader.vue'
import Quiz from './quiz.vue'

const {quiz} = defineProps(['quiz'])
const isLoading = ref(true)

setTimeout(() =>{
      isLoading.value = false
      
}, 4800)
 const good =()=>{
    alert('isjfigdgfergz')
 }
</script>
<template>
 <div class="container">
        <Loader v-if="isLoading" />
        <Quiz v-else class="container mt-5" :quiz="quiz" @return-home="$emit('return-home')"  @return-result="$emit('return-result')"/>
    </div>
</template>
<style scoped>

.ans {
  margin-left: 36px !important;
}

.btn:focus {
  outline: 0 !important;
  box-shadow: none !important;
}

.btn:active {
  outline: 0 !important;
  box-shadow: none !important;
}
</style>