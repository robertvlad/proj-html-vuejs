<script>

// IMPORT COMOPONENTI PAGINA
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';

// IMPORT DATA
import { store } from './store';

export default {

    components: { 

      HeaderComponent, 
      MainComponent, 
      FooterComponent

    },

    data() {
      return {

        store

      }
    },
}

</script>


<template>

  <header>
    <HeaderComponent :links='store.links'/>
  </header>

  <main>
    <MainComponent/>
  </main>

  <footer>
    <FooterComponent :social='store.socialLinks' :courses='store.coursesFooter'/>
  </footer>
  
</template>


<style lang="scss" scoped>

</style>