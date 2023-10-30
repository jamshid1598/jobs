<template>
    <h1>Job Detail Page</h1>
    <hr>
    <div v-if="job">
        <h4>{{ job.title }}</h4>
        <span>{{ id }} - {{ job.id }}</span>
        <span>{{ job.salary }}</span>
        <p>{{ job.description }}</p>
    </div>
    <div v-else>
        <span>job detail loading ...</span>
    </div>
  
</template>

<script>
export default {
    props: [
        'id',
    ],
    data() {
        return {
            // id: this.$route.params.id

            job: null
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs/' + this.id)
            .then((res) => res.json())
            .then((data) => this.job = data)
            .catch((error) => console.log(error.message))
    }
}
</script>

<style>

</style>