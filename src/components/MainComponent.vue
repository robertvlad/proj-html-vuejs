<script>

import FirstMainComponent from './FirstMainComponent.vue';
import SecondMainComponent from './SecondMainComponent.vue';

import { store } from '../store';

    export default {

    name: "MainComponent",

    components: { 

        FirstMainComponent,
        SecondMainComponent

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
        <FirstMainComponent :imgs='store.imgFirstMain'/>
    </div>

    <div>
        <SecondMainComponent/>
    </div>
    
</template>


<style lang="scss" scoped>
    
</style>