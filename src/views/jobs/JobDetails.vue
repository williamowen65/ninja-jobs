<template>
  <h1>Job Details Page {{ id }} </h1>
    <div v-if="job">
      <p> {{ job.title }} </p>
      <p> {{ job.details }} </p>
    </div>
    <div v-else>
      Loading page ....
    </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            // alt way to directly look in url for data
            // id: this.$route.params.id
          job: null
        }
    },
    mounted() {
      fetch(' http://localhost:3000/jobs/' + this.id)
        .then(res => res.json())
        .then(data => this.job = data)
    }
}
</script>

<style>

</style>