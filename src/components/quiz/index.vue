<script setup>
import {defineProps,ref} from 'vue';
import Loader from './loader.vue'
const {quiz} = defineProps(['quiz'])
const isLoading = ref(true)
setTimeout(() => {
      isLoading.value = false
  }, 4800)
</script>
<template>
 <div class="container">
        <Loader v-if="isLoading" />
        <div v-else class="container mt-5">
        <div class="d-flex justify-content-center row">
            <div class="col-md-10 col-lg-10">
                <div class="border">
                    <div class="question bg-white p-3 border-bottom">
                        <div class="d-flex flex-row justify-content-between align-items-center mcq">
                            <h4 style="color:rgb(8, 152, 119);">{{ quiz.name }}</h4><span>(5 of 20)</span></div>
                    </div>
                    <div class="question bg-white p-3 border-bottom">
                        <div class="d-flex flex-row align-items-center question-title">
                            <h3 class="text-danger">Q.</h3>
                            <h5 class="mt-1 ml-2"> {{ quiz.questions[0].text }}</h5>
                        </div><div class="ans ml-2">
<label class="radio"> <input type="radio" name="brazil" value="brazil"> <span>Brazil</span>
</label>    
</div><div class="ans ml-2">
<label class="radio"> <input type="radio" name="Germany" value="Germany"> <span>Germany</span>
</label>    
</div><div class="ans ml-2">
<label class="radio"> <input type="radio" name="Indonesia" value="Indonesia"> <span>Indonesia</span>
</label>    
</div><div class="ans ml-2">
<label class="radio"> <input type="radio" name="Russia" value="Russia"> <span>Russia</span>
</label>    
</div></div>
                    <div class="d-flex flex-row justify-content-between align-items-center p-3 bg-white"><button @click="$emit('return-home')" class="btn btn-primary d-flex align-items-center btn-danger" type="button"><i class="fa fa-angle-left mt-1 mr-1"></i>&nbsp;Exit</button><button class="btn btn-primary border-success align-items-center btn-success" type="button">Next<i class="fa fa-angle-right ml-2"></i></button></div>
                </div>
            </div>
        </div>


       
    </div>






      
    </div>
</template>
<style scoped>
body{
    background-color:#eee;
}

label.radio {
  cursor: pointer;
}

label.radio input {
  position: absolute;
  top: 0; 
  left: 0;
  visibility: hidden;
  pointer-events: none;
}

label.radio span {
  padding: 4px 0px;
  border: 1px solid red;
  display: inline-block;
  color: red;
  width: 100px;
  text-align: center;
  border-radius: 3px;
  margin-top: 7px;
  text-transform: uppercase;
}

label.radio input:checked + span {
  border-color: red;
  background-color: red;
  color: #fff;
}

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