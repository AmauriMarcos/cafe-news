<template>
    <div class="carousel">
    <v-app id="inspire">
        <v-carousel cycle class="carousel-box">
        <v-carousel-item 
            v-for="(item,i) in items"
            :key="i"
            :src="item.src"
            reverse-transition="fade-transition"
            transition="fade-transition"
        ><h2 class="corousel-titulo">{{chamada[i].title}}</h2>
        </v-carousel-item>
        </v-carousel>
    </v-app>
    </div>
</template>

<script>
export default {
    data(){
        return{
        /*   colors: [
                'indigo',
                'warning',
                'pink darken-2',
                'red lighten-1',
                'deep-purple accent-4',
            ], */
            items: [
            {
            src: 'https://tracks-trails.com/wp-content/uploads/2015/07/shutterstock_2550152111.jpg',
            },

            {
            src: 'https://www.washingtonpost.com/resizer/uwlkeOwC_3JqSUXeH8ZP81cHx3I=/arc-anglerfish-washpost-prod-washpost/public/HB4AT3D3IMI6TMPTWIZ74WAR54.jpg',
            },

            {
            src: 'https://myrockstarrant.files.wordpress.com/2018/07/banner-image.jpg?w=1096&h=683',
            },

            {
            src: 'https://global.unitednations.entermediadb.net/assets/mediadb/services/module/asset/downloads/preset/Libraries/Production+Library/11-02-2020_Myanmar_Coronavirus.jpg/image560x340cropped.jpg',
            },

            {
            src: 'https://pix10.agoda.net/hotelImages/7243073/-1/2c23bff22987ee68884d4f4996df672a.png?s=1024x768'
            },

            ],
            chamada: [
					 {
                title: 'Tudo o que você precisa saber antes de visitar o Lago Moraine'
            },
            {
                title: 'O que torna os cães tão especiais e bem-sucedidos?'
            },
            {
                title: 'O sucesso monumental de GTA 5 - terá impacto na futura Rockstar'
            },
            {
                title: 'Coronavírus: China reforça medidas de isolamento e Taiwan registra primeira morte'
            },
            {
                title: 'Conheça a "maior piscina de borda infinita do mundo"'
            }
		 ]

        }
    }
}
</script>

<style lang="scss">
    .carousel{
        grid-column: 8/12;
        grid-row: 4/5;
        width: 100%;
        height: 100%;
        transform: translateY(-3.4rem);
    }
    .corousel-titulo{
        color: white;
        transform: translateY(20rem);
        padding: 2rem;
    }

    .carousel-box{
        border: .5rem solid rgb(235, 235, 235);
    }

    .v-application--wrap{
        min-height: 0 !important;
    }
</style>
