<template>
<div>
    
    <Header></Header>
    <Cover></Cover>
    <OurServices></OurServices> 
    <no-ssr placeholder="Carregando...">
      <Categories></Categories> <!-- TODO: Tornar compatível com SSR, uma versão com apenas CSS pode ser viavel dependendo do caso -->
    </no-ssr>
    <Support></Support>
    <Footer></Footer>

</div>
</template>

<script>
import Header from '~/components/Header.vue';
import OurServices from '~/components/OurServices.vue'
import Categories from '~/components/Categories.vue';
import Cover from '~/components/Cover.vue';
import Support from '~/components/Support.vue';
import Footer from '~/components/Footer.vue';
export default {
  name: 'HomePage',

  components: {
    Header,
    Cover,
    Categories,
    OurServices,
    Support,
    Footer
  }
}
</script>
