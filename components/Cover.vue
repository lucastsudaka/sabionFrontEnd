<style lang="scss" >
@import "~/assets/var.scss";
.cover {
    .right-image {
        float:right;
    }
    .title-main {
        margin-top:20px;
        margin-bottom:35px;
        color:$primary;
    }
    .cover-about {
        font-size:18px;
        line-height:30px;
        color:$primary;
        max-width:70%;
    }
}

</style>
<template>
<div class="cover">
<section class="hero is-medium ">
  <div class="hero-body">
    <div class="main-container">
        <div class="media">
           <div class="media-content">
         
               <h4 class="title-secondary" >A SABION</h4>
               <img  :src="require('~/static/imgs/retangulo.jpg')">
                <div class="title-main is-italic">
                   <h2>"<span>Tornamos o</span> <span class="has-text-weight-bold">digital</span> <span>mais</span> <span class="has-text-weight-bold">humano</span>."</h2>
                </div>
                <div class="cover-about is-italic">
                    A  <span class="has-text-weight-bold">Sabion</span>  é uma Agência Digital  <span class="has-text-weight-bold">full Service</span>
                    especialista em tecnologia e inovação.
                </div>
            

              
            </div>
            <div class="media-right is-hidden-mobile	">
                <img class="right-image" :src="require('~/static/imgs/astronaut.jpg')">
            </div>
                
        </div>
    </div>
  </div>
</section>
</div>
</template>

<script >

export default {
    data: () => ({

    }),
    mounted() {


    }
}
</script>