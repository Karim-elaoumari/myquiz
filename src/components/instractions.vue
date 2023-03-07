<script setup>

</script>

<template>
    <div class="container">
        <div class=" text-center mt-4">
            <h3 style="color:rgb(8, 152, 119);">
                Quiz Instractions
            </h3> 
        </div>
       

       <ul class="fs-5 mt-5 p-2" style="width:70%;margin: auto;">
        <li class="pt-2"> You have 1 min to Answer question</li>
        <li class="pt-2"> You can't go to the next question until you answer to the current Question</li>
        <li class="pt-2"> You will have a Progress bar that show you your Progress</li>
        <li class="pt-2"> You will have Question with One Choice or Multiple Choice</li>
       </ul>
       <div class=" text-center mt-4">
        <button  @click="$emit('return-home')" type="button" class="btn btn-warning">Return</button>
        <button @click="$emit('start-quiz')" type="button" class="btn btn-success ms-3">Start</button>
        
        </div>
    </div>
    
</template>
<style>

</style>