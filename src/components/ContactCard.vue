<template>
  <address class="card">
    <h1 class="card-header">{{ name }}</h1>
  </address>
</template>

<script>
export default {
  name: 'ContactCard',
  props: {
    name: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  background: #ffffff;
  border: 1px solid #dddddd;
  margin-bottom: 15px;
  width: 25%;
  box-shadow: 0 3px 10px 0 rgba(0,0,0,0.24);
  border-radius: 10px;
}
</style>
