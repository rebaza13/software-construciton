<template>
  <button @click="handleClick('title')">order by title</button>
  <button @click="handleClick('salary')">order by salary</button>
  <button @click="handleClick('location')">order by location</button>
  <job-list :jobs="jobs" :order="order"></job-list>
</template>

<script setup>
import { ref } from "vue";
// import type { Job } from "../src/types/Job"; // Import Job interface as type
import JobList from "./components/JobList.vue";
// import type { OrderTerm } from "@/types/OrderTerm";
const jobs = ref([
  { title: "Software Engineer", location: "Iraq", salary: 200000, id: "22" },
  { title: "Data Scientist", location: "Baghdad", salary: 180000, id: "23" },
  { title: "Web Developer", location: "Erbil", salary: 150000, id: "24" },
  { title: "UX Designer", location: "Sulaymaniyah", salary: 160000, id: "25" },
  { title: "Product Manager", location: "Basra", salary: 170000, id: "26" },
]);

const order = ref("title");
const handleClick = (term) => {
  order.value = term;
};
</script>
