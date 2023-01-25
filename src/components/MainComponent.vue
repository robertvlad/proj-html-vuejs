<script>

// IMPORT COMPONENTS
import FirstMainComponent from './FirstMainComponent.vue';
import SecondMainComponent from './SecondMainComponent.vue';
import ThirdMainComponent from './ThirdMainComponent.vue';
import SubscribeComponent from './SubscribeComponent.vue';
import PartnersComponent from './PartnersComponent.vue';

// IMPORT DATA
import { store } from '../store';

    export default {

    name: "MainComponent",

    components: {

        FirstMainComponent,
        SecondMainComponent,
        ThirdMainComponent,
        SubscribeComponent,
        PartnersComponent

    },

    data() {
        return {

            store

        }
    },
}
</script>


<template>

    <div>
        <FirstMainComponent :imgs='store.imgFirstMain' :items='store.faculties'/>
    </div>

    <div>
        <SecondMainComponent/>
    </div>

    <div>
        <ThirdMainComponent/>
    </div>

    <div>
        <SubscribeComponent/>
    </div>

    <div>
        <PartnersComponent :imgs='store.imgPartners'/>
    </div>

</template>


<style lang="scss" scoped>
    
</style>