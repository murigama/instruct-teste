<template>
  <div id="app">
    <header class="header-site">
      <div class="content">
        <div class="logo-site">
          <img alt="Logo Instruct" src="./assets/instruct.svg">
        </div>
        <div class="filter">
            <label for="filter"><b>Filtrar por email:</b></label>
            <select name="" id="filter" v-model="filter">
              <option value="">Todos</option>
              <option v-for="domain in domains" v-bind:key= domain>{{domain}}</option>
            </select>
            {{teste}}
        </div>
      </div>
    </header>
    <section class="list-contacts">
      <Loading v-if="loading"></Loading>
      <div class="content" v-if="!loading">
        <ContactCard v-for="contact in filteredContacts" v-bind:key= contact.id
          :name= "contact.name"
          :username = "contact.username"
          :email = "contact.email"
          :phone = "contact.phone"
          :website = "contact.website"
          :address = "contact.address" 
        ></ContactCard>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios'

import ContactCard from './components/ContactCard.vue'
import Loading from './components/Loading.vue'

export default {
  name: 'app',
  data() {
    return {
      loading: true,
      error: false,
      contacts: [],
      domains: null,
      filter: ''
    }
  },
  methods: {
    getContacts () {
      axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        this.contacts = response.data;
        let allDomains = response.data.map(function(contact) {
          return contact.email.split('.').pop();
        });
        let uniqueDomains = [...new Set(allDomains)];
        this.domains = uniqueDomains;

      })
      .catch(() => {
        this.error = true
      })
      .finally(() => this.loading = false)
    }
  },
  created() {
    this.getContacts();
  },
  computed: {
    filteredContacts: function () {
      return this.contacts.filter( (contact) => {
        return contact.email.match(this.filter);
      })
    }
  },
  components: {
    ContactCard,
    Loading
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
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 15px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.header-site select {
  background-color: #ffffff;
  border: 0;
  padding: 10px 5px;
  border-radius: 5px;
}
.list-contacts .content {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  margin-top: 20px;
}
@media (max-width: 768px) 
{
  .list-contacts .content {
    grid-template-columns: 1fr 1fr;
  }
}
@media (max-width: 425px) 
{
  .list-contacts .content {
    grid-template-columns: 1fr;
  }
}
</style>
