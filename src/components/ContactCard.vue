<template>
  <address class="card">
    <h1 class="card-header">{{ name }}</h1>
    <ul>
      <li><span class="icon-user-outline"></span>{{ username }}</li>
      <li><span class="icon-social-at-circular"></span>{{ email }}</li>
      <li><span class="icon-phone-outline"></span>{{ phone }}</li>
      <li><span class="icon-link-outline"></span> {{ website }}</li>
      <li><span class="icon-location-arrow-outline"></span>{{ address.street }}, {{ address.suite }}, {{ address.city }}, {{address.zipcode}}</li>

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
@import url('../assets/icons/style.css');
h1 {
  margin-top: 0;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
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
