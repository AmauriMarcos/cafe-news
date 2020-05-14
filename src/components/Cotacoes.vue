<template>
    <div class="cotacaoes-box">
        <p v-if='error'>{{error}}</p>

          <div class='dolar' v-if="dolar.rates.BRL > 5.8">
            <p class="moeda">Dólar</p>
            <div>
                <svg class="icon-up" :class="{green: true}">
                    <use xlink:href=".././../public/img/sprite.svg#icon-arrow-up"></use>
                </svg> 
            </div>

            <p class="dolar-result" :class="{green: true}">{{dolar.rates.BRL.toFixed(3)}}</p>                    
        </div>

        <div class="dolar" v-else>
            <p class="moeda">Dólar</p>
            <div>
                <svg class="icon-down" :class="{red: true}">
                    <use xlink:href=".././../public/img/sprite.svg#icon-arrow-down"></use>
                </svg> 
            </div>
             <p class="euro-result" :class="{red: true}">{{dolar.rates.BRL.toFixed(3)}}</p>
        </div>

        <div class='euro' v-if="euro.rates.BRL > 6.3">
            <p class="moeda">Euro</p>
            <div>
                <svg class="icon-up" :class="{green: true}">
                    <use xlink:href=".././../public/img/sprite.svg#icon-arrow-up"></use>
                </svg> 
            </div>

            <p class="euro-result" :class="{green: true}">{{euro.rates.BRL.toFixed(3)}}</p>                    
        </div>

        <div class="euro" v-else>
            <p class="moeda">Euro</p>
            <div>
                <svg class="icon-down" :class="{red: true}">
                    <use xlink:href=".././../public/img/sprite.svg#icon-arrow-down"></use>
                </svg> 
            </div>
             <p class="euro-result" :class="{red: true}">{{euro.rates.BRL.toFixed(3)}}</p>
        </div>
        
    </div>
</template>
<script>
import axios from "axios";
export default {
    data(){
        return{
            dolar: [],
            euro : [],
            error: '',
        }
    },
    mounted(){
        axios.get("https://api.exchangeratesapi.io/latest?base=EUR")
            .then(response =>{
                this.euro = response.data;
            })
            .catch(error => {
                this.error = error;
            })

        axios.get("https://api.exchangeratesapi.io/latest?base=USD")
            .then(response =>{
                this.dolar = response.data;
            })
            .catch(error =>{
                this.error = error;
            })
    }
}
</script>

<style lang="scss" scoped>

    p{
        font-size: .8rem;
    }

    .moeda{
        font-weight: 600;
        margin-right: 10px;
    }
    

    .dolar{
        margin-bottom: 5px;
    }
    
    .red{
        fill: rgb(192, 57, 57);
        color: rgb(192, 57, 57);
    }

    .green{
        fill: #86a760;
        color:#86a760
    }

    .dolar,
    .euro{
        display: flex;
    
        justify-content: space-between;
    }

    .icon-up,
    .icon-down{
        width: .9rem;
        height: .9rem;
    }

    .dolar-result,
    .euro-result{
        margin-left: 3px;
    }

    .euro-result{
        transform: translateX(-.3rem);
    }

    .icon-down{
        transform: translateX(-.1rem);
    }
</style>