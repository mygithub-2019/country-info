<template>
  <div class="container">
      <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
        <ul class="navbar-nav">
          <li class="nav-item">
            <span class="nav-link" href="#">Country and Other Info</span>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" @click="viewType('list')">List</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" @click="viewType('grid')">Grid</a>
          </li>
          <li>
            <!-- <span>{{ new Date().toLocaleString()}}</span> -->
            <input class="form-control" 
              placeholder="Please enter country" 
              type="text"
              v-model="searchClient"
              v-on:input="filteredClients"/>
          </li>
          <li>
            <span class="nav-link">Total Countries: {{ this.countries.length }}</span>
          </li>
        </ul>
      </nav>
      <br>
    <!-- <div>
        <button type="button" class="btn btn-primary" @click="viewType('list')">List</button>&nbsp;&nbsp;
        <button type="button" class="btn btn-primary" @click="viewType('grid')">Grid</button>
      </div> -->
    <div  style="height: 550px; overflow-y: scroll;">
      <div v-if='listViewType'>
        <app-tabl-table-view :COUNTRIES = 'countries'/>
      </div>
      <div v-else>
        <app-grid-view :COUNTRIES = 'countries'/>
      </div>
      <div v-if='countries.length <= countriesLength'>
        <p>{{ noCountryFound }}</p>
      </div>
      <!-- <div v-else>
        <app-country-detail :COUNTRIES = 'countries'/>
      </div> -->
  </div>
  </div>
</template>

<script>
import axios from 'axios'
import TableView from '../views/TableView.vue'
import GridView from '../views/GridView.vue'
import CountryDetail from './CountryDetail.vue'


export default {
  data(){
    return {
      listViewType: true,
      countries: [],
      searchClient: '',
      allCountries: [],
      noCountryFound: 'No country found',
      countriesLength: 0
    }
  },
  computed: {
    
  },
  props: {
    msg: String
  },
  components: {
    appTablTableView: TableView,
    appGridView: GridView,
    appCountryDetail: CountryDetail
  },
  methods: {
    filteredClients() {
        let _c = []
        const search = this.searchClient.toLowerCase().trim();

      if (!search) return this.countries = this.allCountries;

      this.allCountries.filter(item => {
          if(item.name.toLowerCase().indexOf(search) > -1){
            _c.push(item)
          }
      })
      this.countries = _c
      console.log(_c)
    },
    viewType(type){
      debugger
      if(type == 'list'){
        this.listViewType = true
        return
      }
      this.listViewType = false
    },
    getTime(){
      setInterval({
        
      })
    }
  },
  created () {
    axios
      .get('https://restcountries.eu/rest/v2/all')
      .then(response => {
          this.countries = response.data
          this.allCountries = response.data
          console.log('Response: ', response)
      })
      .catch(error => {
          console.log(error)
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
