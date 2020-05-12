<template>
  <div class="jornal">
     <div class="manchete">
        <a :href="noticias.articles[15].url">
           <h1 class="title">{{noticias.articles[15].title}}</h1> 
        </a>     
     </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
   data(){
     return{
       noticias: [],
       error: ''
     }
   },
   methods:{
      getData(){
         axios.get("http://newsapi.org/v2/top-headlines?country=br&apiKey=5103814d494c414f952bfe5f2290191e")
         .then(response => {
            this.noticias= response.data;
         })
         .catch(error =>{
            this.error = error;
         }) 
     }
   },
   mounted(){
      this.getData();
   }
};
</script>

<style lang="scss">
   .jornal{
      grid-column: 2/7;
      grid-row: 4/5;
   }

   .title{
      margin: .6rem 0 .6rem 0;
   }

   a{
      color: black;
      text-decoration: none;
      transition: color .3s ease;
   }

   a:hover{
      color: #D10104;
   }
</style>