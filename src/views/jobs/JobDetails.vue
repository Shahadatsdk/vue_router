<template>
    <div v-if="job">
      <h1>{{ job.title }}</h1>
      <p>{{ job.details }}</p>
    </div>
    <div v-else>
      <p>Loading job details...</p>
    </div>
  </template>

<script>
export default {
    props: ['id'],
    // data() {
    //     return {
    //         id: this.$route.params.id
    //     }
    // }
    data() {
        return {
            jobs: null
        }
    },
    mounted() {
        fetch("http://localhost:3000/jobs" + this.id)
        .then(res => res.json())
        .then(data => this.jobs = data)
        .catch(err => console.log(err.message))
    }
}
</script>

<style>

</style>


