<style lang="scss" >
@import "~/assets/var.scss";
.supportForm {
    text-align:left;
    .field:not(:last-child) {
        margin-bottom:50px;
    }

}
</style>

<template>
<div class="supportForm">
    <section>
        <b-field label="Nome">
            <b-input placeholder="Seu nome"></b-input>
        </b-field>
        <b-field label="E-mail">
            <b-input placeholder="Seu e-mail"></b-input>
        </b-field>
        <b-field label="Mensagem">
            <b-input placeholder="Sua mensagem"></b-input>
        </b-field>
        <b-button  size="is-medium" type="is-primary">Enviar</b-button>
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