<template>
    <div>
        <p v-if='error'>{{error}}</p>
        <div class="bloco_do_tempo">
            <div class="cityName">
                <p>
                   {{weather.name}}
                </p>
                <button class="select" @click="overlay = !overlay">
                     <v-icon class="select_icon">fas fa-angle-down</v-icon>
                </button>     
            </div>
            <div class="temperatura">
                 {{showTemperature()}} °C 
            </div>
             <div class="descricao">
                 <p class="descricao__texto">{{weather.weather[0].description}}</p>
             </div>
            <div class="imagem">
                <img :src="`http://openweathermap.org/img/w/${weather.weather[0].icon}.png`" class="imagem__icon">
            </div>         
        </div>
    </div>
</template>

<script>/*  */
import axios from 'axios';
/* import request from 'request'; */
export default {
    data(){
        return{
            weather: [],
            error: '',
            city: 'Niš',
            absolute: true,
            overlay: false,
        }
    },
    methods: {
        
        getData(){
            /*  api.openweathermap.org/data/2.5/weather?q={city name}&appid={your api key} */
            /*  API key  67cf9d4def2661d430770316daf59449 */
            const apiKey = '67cf9d4def2661d430770316daf59449';
            let city   = this.city;
            console.log(city);
            console.log(apiKey);
            axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&lang=pt_BR`)
            .then(response => {
                this.weather = response.data
            }). catch(error => {
                this.error = error;
            })

         },
         showTemperature(){
             let temperatura = this.weather.main.temp -  273.15;
             temperatura =  Math.round(temperatura);
             return temperatura 
         }
   
  },
   mounted(){
        this.getData();
    }
}
</script>

<style lang="scss">
    .bloco_do_tempo{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        column-gap: 15px;
    }
    .cityName{
        grid-column: 2/-1;
        grid-row: 1/2;
    }
    .temperatura{
        grid-column: 2/-1;
        grid-row: 2/3;
    }

    .descricao{

        grid-column: 2/-1;
        grid-row: 3/4;

        &__texto{
            font-size: .7rem;
            font-weight: 600;
            color: rgb(102, 102, 102);
        }
    }
    
    .imagem{

        grid-column: 1/2;
        grid-row: 1/4;

        &__icon{

        }
    }

    .cityName{
        display: flex;
    }

    .select{
        margin-left: 5px;
        outline: none;
    }

</style>