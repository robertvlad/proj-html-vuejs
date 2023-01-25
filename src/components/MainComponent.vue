<script>

import FirstMainComponent from './FirstMainComponent.vue';

import { store } from '../store';

    export default {

    name: "MainComponent",

    components: { 

        FirstMainComponent 

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
    
</template>


<style lang="scss" scoped>
    
</style>