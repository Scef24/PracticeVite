<script setup>
import {ref} from 'vue'
const message = ref('Hello')
let res = ref('')
let num = ref('')

const grade =()=>
{
    if(num.value == null) {
        res.value = 'Invalid Input'
        return;
    }

    if(num.value > 60) {
        res.value = "Pass"
    }
    else {
        res.value = "Fail"
    }
}
</script>

<template>
<div>
    <p>{{ message }}</p>
    <h1>Enter your Grade</h1>
    <input type="number" v-model="num">
    <input type="submit" value="Validate" @click="grade">
    <br>
    <h3 :class="{'pass' :res== 'Pass', 'fail' :  res =='Fail'}">{{ res || 'No input'}}</h3>
</div>
</template>

<style>
.pass {
    color: green;
}
.fail {
    color: red;
}
</style>