<template>
    <header>
    <nav class="navbar">
        <h4>Cafe News</h4>
    </nav>
    <div class="info-head">
        <div class="info-head--options">
            <div class="myLogo">
                <svg class="icon">
                     <use xlink:href=".././../public/img/sprite.svg#icon-renren"></use>
                </svg>
                <div class="dizeres">
                    <span class="dizeres__cafe">KFÉ</span>
                    <span class="dizeres__conteudo">o melhor conteúdo</span>
                </div> 
            </div>
           
            <div class="cadastro">
                <input type="text" class="cadastro__usuario" placeholder="Usuário">
                <input type="text" class="cadastro__senha" placeholder="Senha">
                <button class="cadastro__btn">Entrar</button>
            </div>

            <div class="cotacoes">
                <Cotacoes></Cotacoes>
            </div>
            

            <p>Tempo</p>
            <p>Busca</p>       
        </div>   
        <hr>  
    </div>
    </header> 
</template>

<script>
import Cotacoes from "./Cotacoes";
export default {
    components: {
        Cotacoes
    }
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

    .myLogo{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .icon{
        width: 4.5rem;
        height: 4.5rem;
        fill: firebrick;
    }

    .dizeres{
        display: flex;
        flex-direction: column;

        &__cafe{
            font-size: 4.5rem;
            font-weight: 700;
        }

        &__conteudo{
            margin: 0;
            transform: translateY(-1rem);
            font-weight: 600;
        }
    }



    .cadastro{
        display: flex;
        justify-content: center;
        align-items: center;

        &__usuario{
            
        }

        &__senha{

        }

        &__senha,
        &__usuario{
            width: 120px;
            height: 40px;
            outline: none;
            border: 1px solid #ccc;
        }

        &__btn{
            width: 110px;
            height: 40px;
            background: linear-gradient(to right, #D10104, rgb(255, 231, 14));
            color: white;
            text-transform: uppercase;
            font-size: .8rem;
        }
    }

    .cotacoes{
        display: flex;
        justify-content: start;
        align-items: center;
    }

    ::placeholder{
         transform: translateX(1rem);
        font-size: .9rem;
    }
    
</style>