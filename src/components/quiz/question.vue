<script setup>
import {defineProps} from 'vue';
const {question} = defineProps(['question'])
</script>

<template>
        <h3 class="text-danger">Q.</h3>
         <h5 class="mt-1 ml-2"> {{ question.text }}</h5>
</template>
<style scoped>
</style>