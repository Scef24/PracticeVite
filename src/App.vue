<script setup>
import {ref} from 'vue'

const name = ref('')
const ave = ref('')
const students = ref([])
const compute = ref('')
let message = ('')
const Check = ()=>{

    if(ave.value < 60) {
  students.value.push({fname:name.value, average:ave.value, compute:"Fail"})
}
 else {
    students.value.push({name:name.value, average:ave.value, compute:"Pass"})
 }
  name.value = ''
  ave.value = ''

}

</script>

<template>
<header>
  <h1>Oral</h1>
</header>
<div>
  <input type="text" v-model= "name" placeholder="Enter Student Name">
  <input type="number" v-model = "ave" placeholder="Average">
  <input type="submit" value="Enter" @click="Check">

  <table >
    <thead>
      
        <th>Name</th>
        <th>Average</th>
        <th>Pass or Fail</th>
    </thead>
    <tbody v-for ="(student,index) in students" :key="index" >
      
        <td>{{ student.fname }}</td>
        <td>{{ student.average }}</td>
        <td :class="{'pass' :student.compute =='Pass', 'fail' :student.compute=='Fail'}" >
        {{ student.compute }}</td>
    </tbody>
  </table>
</div>
</template>

<style>

.fail {
 background-color: red;
}
.pass {
    background-color: green;
}
body{
    background-color: white;
    color: black;
}
table {
    border:1px solid black
}
th,td{
    border:1px solid black
}

</style>