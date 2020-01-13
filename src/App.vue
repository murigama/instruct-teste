<template>
  <div id="app">
    <header class="header-site">
      <div class="content">
        <div class="logo-site">
          <img alt="Logo Instruct" src="./assets/instruct.svg">
        </div>
        <div class="filter">
            <label for="filter"><b>Filtrar por email:</b></label>
            <select name="" id="filter">
              <option value="">Todos</option>
            </select>
        </div>
      </div>
    </header>
    <section class="list-contacts">
      <div class="content">
        <ContactCard v-for="contact in contacts" v-bind:key= contact.id
          v-bind:name= "contact.name"
        ></ContactCard>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios'

import ContactCard from './components/ContactCard.vue'

export default {
  name: 'app',
  data() {
    return {
      loading: true,
      contacts: [],
      domains: null
    }
  },
  methods: {
    getContacts () {
      axios
      .get('http://jsonplaceholder.typicode.com/users')
      .then(response => {
        /* eslint-disable no-console */
        console.log(response.data);
        /* eslint-enable no-console */
        this.contacts = response.data
      })
      // .catch(error => {
      //   console.log(error)
      //   //this.errored = true
      // })
      .finally(() => this.loading = false)
    }
  },
  created() {
    this.getContacts();
  },
  components: {
    ContactCard
  }
}
</script>

<style>
body {
  margin: 0;
  background: #f2f2f2;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.header-site {
  background: #23A5FA;
  background: -moz-linear-gradient(45deg, #1e73aa 0%, #23a5fa 100%);
  background: -webkit-linear-gradient(45deg, #1e73aa 0%, #23a5fa 100%);
  background: linear-gradient(45deg, #1e73aa 0%, #23a5fa 100%);
}
.header-site .content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 15px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
