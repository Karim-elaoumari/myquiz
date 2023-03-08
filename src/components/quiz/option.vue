<script setup>
import {defineProps} from 'vue';
const {option, iscorrect,selected_option_id} = defineProps(['option','iscorrect','selected_option_id'])
</script>



<template>
         <button type="button" v-if="selected_option_id==option.id" class="btn p-3 w-50 mt-2"  :class="iscorrect" @click="$emit('selected-option',option.id)" :disabled="selected_option_id">{{option.text}}</button>   
         <button type="button" v-else class="btn btn-secondary p-3 w-50 mt-2" @click="$emit('selected-option',option.id)" :disabled="selected_option_id">{{option.text}}</button>   
</template>



<style scoped>
  button[disabled] {
    opacity: 1;
    pointer-events: auto;
  }
</style>

