<template>
  <h1>Jobs</h1>
  <div v-if="jobs.length">
    <div v-for="job in jobs" v-bind:key="job.id" class="job">
        <router-link v-bind:to="{ name: 'JobDetail', params: { 'id':  job.id} }">
            <h4>{{ job.title }}</h4>
        </router-link>
    </div>
  </div>
  <div v-else>
    <span>Jobs loading ...</span>
  </div>
</template>

<script>
export default {
    data() {
        return {
            jobs: []
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs')
            .then((res) => res.json())
            .then((data) => this.jobs = data)
            .catch((error) => console.log(error.message))
    }
}
</script>

<style>
.job h4 {
    background: #e4e4e4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
}
.job h4:hover {
    background: #ddd;
}
.job a {
    text-decoration: none;
}
</style>