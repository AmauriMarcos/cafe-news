<template>
    <div>
        <p v-if='error'>{{error}}</p>
        <div>
            {{weather}}
        </div>   
    </div>
</template>

<script>
import axios from 'axios';
/* import request from 'request'; */
export default {
    data(){
        return{
            weather: [],
            error: ''
        }
    },
    methods: {

        getData(){
            axios.get('https://api.climacell.co/v3/locations', {
                params: {  
                  /*   limit: '50',
                    offset: '0', */
                    lat: '42.3826',    
                    lon: '-71.1460',
                   
                   /*  unit_system: 'si', */
                    apikey: 'bZRHLJtmhTFtR9zELYq2gcFodQS9dSo3'          
                }
            })
            .then(response =>{
                this.weather = response
            })
            .catch(error => {
                this.error = error;
            })
        }
    },
    mounted(){
        this.getData();
    }
}
</script>

<style lang="scss">

</style>