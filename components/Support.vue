<style lang="scss" >
@import "~/assets/var.scss";
.support {
    position:relative;
    margin-top:70px;
    margin-bottom:70px;
    .support-container-column {
        height:600px;
    }
    .left-column {
        background-color:$primary;
        height:600px;
    }
    /*regras para desktop */
     @media (min-width: 768px) { 
        .support-container {
            width:100%;
            padding-top:50px;
            height:100%;
            right:0;
            top:0;
            position:absolute;
            .box-in {
                height:500px;
                .box-in-columns  {
                    height:500px;
                    text-align:right;
                    .support-content {
                        max-width:65%;
                        margin-left:auto;
                        margin-right: 50px;
                    }
                }
                .right-column {
                    background-color:#fff;;
                    height:100%;
                    box-shadow:0 2px 4px rgba(0,0,0,0.1);
                    border-radius:10px;
                    .form-cointainer {
                        width:50%;
                        padding:25px;
                    }

                }
            }
        }
        .title-main {
            margin-top:20px;
            margin-bottom:35px;
            font-weight:bold;
            color:#fec300;
        }
        .support-about {
            font-size:18px;
            line-height:30px;
            color:#fff;
            max-width:50%;
            margin-left:auto;

        }
    }

    /* responsivo */
    @media (max-width: 768px) { 
        .support-container {
            padding-right:30px;
            padding-left:30px;
        }
        
    }

}

</style>
<template>
<div class="support">
    <div class=" is-hidden-mobile columns support-container-column is-centered is-vcentered">
        <div class="column left-column is-two-thirds">
            <div class="">
            </div>
        </div>
        <div  class="column">
            
        </div>
    </div>
    <div class="support-container">
        <div class="box-in">
            <div class="box-in-columns   is-marginless columns is-centered is-vcentered">
                <div class="column ">
                    <div class="support-content">
                        <div class="title-main is-italic">
                                <h2>Como podemos te ajudar?</h2>
                            </div>
                            <div class="support-about is-italic">
                                Entre em contato  com um de
                                nossos especialistas para que
                                encontremos uma solução
                            </div>
                    </div>
                </div>
                <div  class="column right-column  is-vcentered">
                    <div class="form-cointainer">
                        <SupportForm></SupportForm>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script >
import SupportForm from '~/components/SupportForm.vue';
export default {
    components: { SupportForm },
    data: () => ({

    }),
    mounted() {


    }
}
</script>