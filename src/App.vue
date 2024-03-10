<script setup>
import { ref } from "vue";

const name = ref("");
const ave = ref("");
const students = ref([]);
const compute = ref("");
let message = "";
const Check = () => {
  if (ave.value >= 75) {
    message = "Pass";
  } else {
    message = "Fail";
  }
  students.value.push({
    fname: name.value,
    average: ave.value,
    compute: message,
  });
  name.value = "";
  ave.value = "";
  message = "";
};
</script>

<template>
  <!-- BEGIN: No changes in this section -->
  <header>
    <h1>Oral</h1>
  </header>
  <div>
    <input type="text" v-model="name" placeholder="Enter Student Name" />
    <input type="number" v-model="ave" placeholder="Average" />
    <input type="submit" value="Enter" @click="Check" />

    <table>
      <thead>
        <th>Name</th>
        <th>Average</th>
        <th>Pass or Fail</th>
      </thead>
      <tbody v-for="(student, index) in students" :key="index">
        <td>{{ student.fname }}</td>
        <td>{{ student.average }}</td>
        <td
          :class="{
            pass: student.compute == 'Pass',
            fail: student.compute == 'Fail',
          }"
        >
          {{ student.compute }}
        </td>
      </tbody>
    </table>
  </div>
  <!-- END: No changes in this section -->
</template>

<style>
body {
  font-family: Arial, sans-serif;
}

header {
  background-color: #f8f9fa;
  padding: 20px;
  margin-bottom: 20px;
}

input[type="text"],
input[type="number"] {
  padding: 10px;
  margin: 10px 0;
  border-radius: 4px;
  border: 1px solid #ccc;
}

input[type="submit"] {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 15px;
  text-align: left;
}

.fail {
  background-color: red;
}
.pass {
  background-color: green;
}
body {
  background-color: white;
  color: black;
}
table {
  border: 1px solid black;
}
th,
td {
  border: 1px solid black;
}
</style>
