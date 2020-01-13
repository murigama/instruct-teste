<template>
  <address class="card">
    <h1 class="card-header">{{ name }}</h1>
    <ul>
      <li>{{ username }}</li>
      <li>{{ email }}</li>
      <li>{{ phone }}</li>
      <li>{{ website }}</li>
      <li>{{ address.street }}, {{ address.suite }}, {{ address.city }}, {{address.zipcode}}</li>

    </ul>
  </address>
</template>

<script>
export default {
  name: 'ContactCard',
  props: ['name', 'username', 'email', 'address', 'phone', 'website']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  background-color: #ffffff;
  border: 1px solid #dddddd;
  box-shadow: 0px 2px 1px -1px rgba(0, 0, 0, 0.2), 0px 1px 1px 0px rgba(0, 0, 0, 0.14), 0px 1px 3px 0px rgba(0,0,0,.12);
  border-radius: 5px;
  margin: 0 10px;
  margin-bottom: 15px;
  padding: 16px;
}
</style>
