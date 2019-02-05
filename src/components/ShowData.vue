<template>
  <div>
    
    <h1>Hello</h1>
    <ul>
         <li v-for="result in results"> 
             {{result}}
         </li>  
      
    </ul>
    
   
   
  </div>
</template>

<script>
  import { AUTORA_KEY } from '../config';
  import axios from 'axios';


  export default {
    name: 'ShowData',
    data: function() {
      return {
        key: AUTORA_KEY,
        results: []
      }
    },
    mounted: function() {

      const config = {
        headers: this.key
      }

      var bodyParams = {
        key: "value"
      }
      
      
      const inst = axios.create({headers: { 'Authorization': 'Bearer '+ this.key} })
      inst.get('https://api.autoura.com/api/stops/search?group_context=friends&stop_types=food').then(r => {
        this.results = r.data.response;
      }).catch(e => {
        console.log(e);
      })
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
