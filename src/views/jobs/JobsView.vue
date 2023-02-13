<template>
  <h1>Jobs:</h1>
  <div v-for="job in jobs" :key="job.id">
    <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
      <p>{{ job.title }}</p>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs")
      .then((res) => res.json())
      .then((data) => (this.jobs = data))
      .catch((error) => console.log(error.message));
  },
};
</script>

<style scoped>
p{
    background-color: gray;
    border-radius: 20px;
    padding: 15px;
    width: 40%;
    margin: 10px auto;
    text-decoration: none;
    
}
a{
    text-decoration: none;
    color: white;
    font-weight: bold;
}
</style>
