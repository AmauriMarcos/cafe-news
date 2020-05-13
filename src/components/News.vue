<template>
  <div class="jornal">
     <div class="manchete">
        
      <a :href="noticias.articles[15].url">
         <h1 class="title">{{noticias.articles[15].title}}</h1> 
      </a>

      <ul>
         <li>
           <a :href="noticias.articles[5].url">{{noticias.articles[5].title}}</a>
         </li>
         <li>
           <a :href="noticias.articles[6].url">{{noticias.articles[6].title}}</a>
         </li>
         <li>
           <a :href="noticias.articles[7].url">{{noticias.articles[7].title}}</a>
         </li>
         <li>
           <a :href="noticias.articles[8].url">{{noticias.articles[8].title}}</a>
         </li>
      </ul>
             
     </div>
    
     <div class="blocos">    
         <div class="chamadas" v-for='noticia in noticias' :key='noticia.articles'>
            <div v-for='materia in noticia' :key='materia.title' >
               <div v-if='materia.urlToImage' class="bloc">
                  <a :href="materia.url"><img :src="materia.urlToImage" class="thumb"></a>
                  <a :href="materia.url"><h2 class="materiaSub">{{materia.title}}</h2></a>     
                  <a :href="materia.url"><p>{{materia.description}}</p></a>      
               </div>     
            </div>    
         </div>      
     </div>

     <div class="bloquinho">
          <div class="chamadinha" v-for='noticia in noticias' :key='noticia.articles'>
            <div v-for='materia in noticia' :key='materia.title' >
               <div v-if='materia.urlToImage' class="bloc">
                  <a :href="materia.url"><img :src="materia.urlToImage" class="mini-thumb"></a>
                  <a :href="materia.url"><h5>{{materia.title}}</h5></a>   
               </div>     
            </div>    
         </div>   
     </div>

  </div>
</template>

<script>
import axios from 'axios';
export default {
   data(){
     return{
       noticias: [],
       error: '',
       littleArray: []
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
      },
      showArray(arr){
         this.littleArray = arr.slice(2,6);
         
      }
   },
   mounted(){
      this.getData();
   }
};
</script>

<style lang="scss">
   
   .jornal{
      grid-column: 2/8;
      grid-row: 4/5;
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      row-gap: 15px;
      column-gap: 25px;
   }

   .manchete{
      grid-column: 1/-1;
      grid-row: 1/2;
      
   }

   .blocos{
      grid-column: 1/6;
      grid-row: 2/3;  
   }

   .bloquinho{
      grid-column: 6/8;
      grid-row: 2/3;  
   }

   .bloquinho::before{
      border-top: 1px solid #ccc;
      display: inline-block;
      margin: 1rem 0 1rem 0;
      content: "";
      width: 100%;
   }

   .chamadinha{
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
   }

   .blocos::before{
      border-top: 1px solid #ccc;
      display: inline-block;
      margin: 1rem 0 1rem 0 ;
      content: "";
      width: 100%;
   }

   .chamadas{
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      column-gap: 25px;
     
   }

   .mini-thumb{
      width: 100%;
      object-fit: cover;
      height: 90px;
   }

   .thumb{
      width: 100%;
      object-fit: cover;
      height: 120px;
     
   }
      
   .materiaSub{
      margin: .6rem 0 .5rem 0;
      font-size: 1rem;
   }

   .bloc{
      margin: .7rem 0 .7rem 0;
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

   ul{
      list-style: none;
   }

   li{
      margin: 5px 0 5px 0;
   }
</style>