<style lang="scss" >
@import "~/assets/var.scss";
.footer {
    background-color:#fff;
    .header-frontend {
        font-size:27px;
        font-weight:300;
        color:$primary;
        margin-top:15px;
    }
    .developer-challenge {
        font-size:27px;
        color:$primary;
        font-weight:bold;
    }
}
</style>

<template>
<div class="footer">
    <div class="has-text-centered">
        <img  :src="require('~/static/imgs/logo-icon.jpg')">
        <div class="header-frontend is-italic">&lt;front-end&gt;</div>
        <div class="developer-challenge  is-italic">developerchallenge</div>
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