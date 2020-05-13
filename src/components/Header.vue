<template>
    <header>
    <nav class="navbar">
        <h4>Cafe News</h4>
    </nav>
    <div class="info-head">
        <div class="info-head--options">
            <h2>LOGO</h2>
            <p>Usuario e Senha</p>
            <p>Cotacoes</p>
            <p>Tempo</p>
            <p>Busca</p>       
        </div>   
        <hr>  
    </div>
    </header> 
</template>

<script>
export default {
    
}
</script>

<style lang="scss">
    header{
        grid-column: 1/13;
        grid-row: 1/2;
        
    }
    h4{
        color: white;
        font-size: 1.2rem;
        padding: .5rem;
        text-align: center;
    }
    .navbar{
        background-color: black;
    }

    .info-head{
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        margin: 1rem 0 1rem 0;

         &--options{
            grid-column: 2/12;
            display: flex;
            justify-content: space-around;
        }

        hr{
            grid-column: 2/12;
            border: 2px solid rgb(37, 37, 37);
        }
    }
   
</style>