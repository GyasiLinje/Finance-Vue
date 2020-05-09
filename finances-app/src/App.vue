<template>
<div id="app" class="small-container">
<h1>Employees</h1>
 <div v-for="currencies in data">
{{ currencies.code}}
{{ currencies.rate || currencydecimal}}
 </div>
<!-- <employee-table :employees="employees"/> -->

</div>

</template>

<script>
import axios from 'axios';
//import EmployeeTable from './components/Currency.vue'

export default {
  name: 'app',
  data() {
    return {
      data: []
    }
  },

components: {
 // EmployeeTable,
},


filters: {
  currencydecimal (value) {
    return value.toFixed(2)
  }
},
 mounted() {
   axios
     .get('https://api.coindesk.com/v1/bpi/currentprice.json')
     .then(response => (this.data = response.data.bpi))
 },


}
</script>

<style>

button {
   background: #009435;
    border: 1px solid #009435;
}

  .small-container {
    max-width: 680px;
  }
</style>