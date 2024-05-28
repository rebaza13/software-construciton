<template>
  <div class="job-list">
    <h2>{{ order }}</h2>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
            aspernatur recusandae nemo tempora placeat laboriosam soluta in fuga
            culpa nobis nostrum totam corrupti, voluptatem non velit nisi. Quae,
            quis tempora?
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>
<script setup >

// import type { Job } from "@/types/Job";
// import type { OrderTerm } from "@/types/OrderTerm";
import { computed } from "vue";
const props = defineProps({
  jobs: {
    type: Array ,
    required: true,
    default: () => [], // Providing a default value
  },
  order: {
    type: String ,
    required: true,
  },
});

const orderedJobs = computed(() => {
  return [...props.jobs].sort((a, b) => {
    return a[props.order] > b[props.order] ? 1 : -1;
  });
});
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
.list-move {
  transition: all 1s;
}
</style>
