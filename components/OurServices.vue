<style lang="scss" >
@import "~/assets/var.scss";
.serviceName {
    font-weight: bold;
    font-size:24px;
    line-height:30px;
    margin-top:30px;
}
.service-column {
    margin-bottom:60px;
}
</style>

<template>
<div>
<div class="has-text-centered">
    <h4 class="title-secondary" >SOMOS 360º</h4>
    <img  :src="require('~/static/imgs/retangulo.jpg')">
</div>
<section class="section">
    <div class="main-container">
        <div class="columns is-multiline is-centered is-vcentered ">
            <div 
                v-for="(service, index) in ourServices"                
                :data="service"
                :key="`service-${index}`"   
                class="column service-column is-one-third has-text-centered">  
                <img :src="require('~/'+service.img)">				
                <h4 class="serviceName">{{service.name}}</h4>
            </div>
        </div>
    </div>
    <div class="has-text-centered">
        <img  :src="require('~/static/imgs/retangulo.jpg')">
    </div>
 </section>
</div>
</template>

<script >

export default {
    data: () => ({
        ourServices : [
            {name:'INTELIGÊNCIA ARTIFICIAL', img: 'static/imgs/ai1.jpg' },
            {name:'UX/UI DESIGN', img: 'static/imgs/uiux.jpg' },
            {name:'DESENVOLVIMENTO', img: 'static/imgs/dev.jpg' },
            {name:'LINKS PATROCINADOS', img: 'static/imgs/links.jpg' },
            {name:'SEO',  img: 'static/imgs/seo.jpg'},
            {name:'WEB ANALYTICS / B.I.',  img: 'static/imgs/analytics.jpg'},
            {name:'CRIAÇÃO DE APPS',  img: 'static/imgs/apps.jpg' },
            {name:'CAMPANHAS',  img: 'static/imgs/campanhas.jpg'},
            {name:'REDES SOCIAIS',  img: 'static/imgs/social.jpg'},
        ]
    }),
    mounted() {


    }
}
</script>