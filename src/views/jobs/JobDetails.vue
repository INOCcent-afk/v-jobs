<template>
  <div v-if="job">
    <h1>{{ job.name }}</h1>
    <p>{{ job.website }}</p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  props: ["id"],

  data() {
    return {
      job: null,
    };
  },

  mounted() {
    fetch("http://jsonplaceholder.typicode.com/users/" + this.id)
      .then((response) => response.json())
      .then((data) => (this.job = data))
      .catch((err) => console.error(err.message));
  },
  // data() {
  //   return {
  //     id: this.$route.params.id,
  //   };
  // },
};
</script>

<style></style>
