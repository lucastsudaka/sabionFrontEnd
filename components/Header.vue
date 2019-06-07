<style lang="scss" >
@import "~/assets/var.scss";
.header {
    padding-top:150px;
    padding-bottom:50px;
    background-color:#fff;
    .header-frontend {
        font-size:65px;
        line-height:75px;
        font-weight:300;
        color:$primary;
        margin-top:20px;
        margin-bottom:20px;
    }
    .developer-challenge {
        font-size:65px;
        line-height:75px;
        color:$primary;
        font-weight:bold;
        .is-yellow {
            color:#fdc500;
        }
    }

}
@media (max-width: 768px) {
    .header {
        .header-frontend {
            font-size:40px;
            line-height:50px;
        }
        .developer-challenge {
            font-size:30px;
            line-height:40px;
        }
    }
}
</style>

<template>
<div class="header">
    <div class="has-text-centered">
        <img  :src="require('~/static/imgs/logo.jpg')">
        <div class="header-frontend is-italic">&lt;front-end&gt;</div>
        <div class="developer-challenge  is-italic"><span class="is-yellow">developer</span>challenge</div>
        
    </div>
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