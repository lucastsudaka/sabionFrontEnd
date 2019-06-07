<style lang="scss" scoped>
@import "~/assets/var.scss";
.categories {
    /* ------- tabs */
    .categories-tab ul {
        position:relative;
        text-align:center;
        list-style: none;
        height:40px;    
        margin-bottom:76px;
        li {
            display: inline;
            padding-right:50px;
            padding-left:50px;
            font-size:18px;
        }
        .tab-slider {
            display:inline-block;
            width:30px;
            height:5px;
            border-radius:3px;
            background-color:$primary;
            position:absolute;
            z-index:1200;
            bottom:0;
            transition:all .4s linear
        }
        
    }
    /* tabs responsivo */
    @media (max-width: 768px) { 
        .categories-tab ul {
            height:auto;
            display:flex;
            flex-direction: column;
            li {
                width: 100%;       
                padding-top:15px;
                padding-bottom:15px;
            }
            li a {
                font-size:22px;

            }
            li.is-active {
                background-color:#e5e5e5;
                border-radius:5px;

            }
            .tab-slider  {
                display:none;
            }
        }

    }

    /* ------- masonry  */    
    .masonry { 
        margin-right:-20px;
        .grid-sizer   {
            width:25%;
        }
    .item {
            width:25%;
            height:350px;        
            margin-bottom:20px;
            float: left;
            padding-right:40px;
        
            &.big {
                height:400px;  

            }
            .content {
                height:100%;
                margin-right:-20px;
                border-radius:10px;
                
            }
    }
    }
    /* masonry responsivo */
    @media (max-width: 768px) { 
        .masonry { 
            .item  {
                width:100%;
            }
            .grid-sizer {
                width:100%;
            }

        }
    }

    /* simples animação para os items */
    .list-item {
    display: inline-block;
    margin-right: 10px;
    }
    .list-enter-active, .list-leave-active {
    transition: all 1s;
    }
    .list-enter, .list-leave-to  {
    opacity: 0;
    transform: translateY(30px);
    }
    .title-main {
        margin-top:20px;
        margin-bottom:20px;
        color:$primary;
    }
}
</style>

<template>
<div class="categories">
    <div class="has-text-centered">
        <div class="title-main is-italic"><h2><span>Criamos</span> <span class="has-text-weight-bold">experiências</span></h2></div>
    </div>
    <section class="section">
        <div class="main-container">
            <!-- tabs, usando as tabs do Bulma -->
            <div class="categories-tab is-centered">
                <ul>
                    <li @click="switchCategory('All')" :class="selectedCategory == 'All' ? 'is-active': ''"><a id="tab-category-All" >All</a></li>
                    <li v-for="(category, index) in categories"                    
                        :class="[selectedCategory == category.id ? 'is-active': '']"                   
                        :data="category"
                        :key="`category-${index}`"         
                        @click="switchCategory(category.id)"             
                        :label="category.name">
                            <a  :id="'tab-category-'+category.id">{{category.name}}</a>
                            <div class="tab-slider"></div>
                        
                    </li>
                </ul>
            </div>

            <!-- masonry, usando uma lib "masonry" -->    
            <div ref="masonry" class='masonry' >
                 <div class="grid-sizer"></div> 
                <!-- iterando os itens -->
                <!-- Caso o index do item seja um numero PAR, a classe "big" será adicionada.
                Isto poderia ser feito com CSS, proém acredito que está forma seja mais eficiente.-->
                <transition-group name="list" tag="div">
                <div v-for="(item, index) in filteredItems()"
                    class="item"
                    :class="(index) % 2 == 0 ? ' big ' : '  '"                     
                    :data="item"
                    :key="`fic-${index}`"   >  
                                        
                        <div class="content"
                            :style="{backgroundColor: findCategory(item.category_id).color}">
                            {{index}}
                        </div>
                </div>
                </transition-group>
            </div>
        </div>
    </section>
 </div>
</template>

<script>
import { vueWindowSizeMixin } from 'vue-window-size';


export default {
    mixins:[vueWindowSizeMixin],
    data: () => ({
        selectedCategory : "All",
        //categorias e suas propriedades    
        categories:[
            {name:"Purple", id:1, color: '#c678ff'},
            {name:"Yellow", id:2, color: '#ffe36e'},
            {name:"Grey", id:3, color: '#959595'},
        ],        
        //lista de items
        items:[
            {category_id:1},
            {category_id:2},
            {category_id:1},
            {category_id:3},
            {category_id:2},
            {category_id:1},
            {category_id:3},
            {category_id:1},
            {category_id:2},
            {category_id:1},
            {category_id:2},
            {category_id:1}
        ]
    }),

    methods: {
        //metodo pata retornar a categoria de um item
        findCategory(category_id) {
            return this.categories.find(x => x.id === category_id);  
        },
        switchCategory(category_id) {
            this.selectedCategory = category_id;
            this.domSlideCategory();
            // usnado jquery

        },
        domSlideCategory() {
            const el = $('#tab-category-'+this.selectedCategory); //FIXME -> Utilizar refs!
            var position = el.parent().position();
            var width = el.parent().outerWidth();
            $(".tab-slider").css({"left":+ position.left,"width": width});
        },
        filteredItems() {
            // precisamos adicionar a queue para a alteração no DOM;
            setTimeout(() => {
                this.domMasonry();
            },1);
            if(this.selectedCategory === "All") {
            return  this.items;
            } else {
            return this.items.filter(x => x.category_id == this.selectedCategory);
            }
        },
        domMasonry() {
            if(this.windowWidth > 1) {
                // o element que será utilizado na masonry
                const masonryEl= this.$refs.masonry;
                // nosso import do Masonry  foi feito nas configs do Nuxt
                // vamos instanciar
                const msnry = new Masonry( masonryEl, {
                    itemSelector: '.item',
                    columnWidth: '.grid-sizer',
                    percentPosition: true,
                    horizontalOrder: true
                });
                msnry.reloadItems()
            }
 

        }
    },
    watch: {
        windowWidth: {
            immediate:true,
            handler(newV) {
                setTimeout(() => {
                    this.domMasonry();        
                    this.domSlideCategory();
                },0);
            }
        }
    },
    mounted() {


    }
}
</script>