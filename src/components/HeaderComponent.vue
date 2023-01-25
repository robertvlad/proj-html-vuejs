<script>

    export default {

    name: "HeaderComponent",

    props: {

        links: Array,
        
    },
}
</script>


<template>

    <div class="header">
        <div class="background-red d-flex justify-content-center">
            <nav class="nav-bar container-fluid d-flex align-items-end justify-content-between">
                <img src="../../public/img/theme_eduprime_logo.png" alt="EduPrime" class="logo">
                <div class="d-flex align-items-end">
                    <ul class="d-flex">
                        <li v-for="(link, index) in links" :key="index" class="me-5 d-flex">
                            <a :href="link.url" :class="{ 'active': link.current }">{{ link.title }}</a>
                            <span v-if="link.arrow" :class="{ 'active': link.current }"><i class="fa-solid fa-sort-down"></i></span>
                        </li>
                    </ul>
                    <a href="#">
                        <span class="view button text-uppercase">view courses</span>
                    </a>
                </div>
            </nav>
            <div class="d-flex">
                <div class="d-flex flex-column justify-content-center align-items-center text-center">
                    <div class="title col-7">
                        <h1 class="display-4 fw-bold mb-5">Key to your success</h1>
                        <p>EduPrime is the most versatile WordPress Theme for educational purposes, showcasing universities, courses, secondary schools etc.</p>
                    </div>
                    <div class="fw-bold mt-5">
                        <a href="#"><span class="button btn-courses me-5"><i class="fa fa-search me-2"></i> Search courses</span></a>
                        <a href="#"><span class="button btn-apply"><i class="fa fa-user-plus me-2"></i> Apply for university</span></a>
                    </div>
                </div>
            </div>
            <div class="wave-header">
                <img src="../../public/img/Wave-1.png" alt="Wave">
            </div>
        </div>
    </div>

</template>


<style lang="scss" scoped>

@use '../assets/style/partials/variables' as *;
@use '../assets/style/partials/mixins' as *;

/* GENERALI */
a {
    color: $white;
}

span {
    color: $white;
    margin-left: 10px;
    font-size: 12px;
    cursor: pointer;
}

.button {
    @include button-general;
}


/* SPECIFICHE */

.header {
    height: 700px;
    background: url('../../public/img/theme_slider2_bg-1.jpg');
    position: relative;

    .background-red {
        background-color: $pink2;
        height: inherit;
        position: relative;

        .nav-bar {
            position: absolute;
            top: 0;
            padding: 50px;
            font-weight: bold;

            .logo {
            width: 300px;
            }
        }
    }

    .title {
        color: $white;

        p {
            font-size: 18px;
        }
    }

    .wave-header {
        position: absolute;
        bottom: 0;
        z-index: 1;
    }
}
/* ELEMENTI CON HOVER */

.btn-apply {
    background-color: $white;
    color: $pink2;

    &:hover {
        background-color: $yellow;
        color: $white;
        transition: 0.3s ease-in;
    }

    &:not(:hover) {
        transition: 0.3s ease-out;
    }
}

.btn-courses {
        background-color: $yellow;
        color: $white;

    &:hover {
        background-color: $white;
        color: $pink2;
        transition: 0.3s ease-in;
    }

    &:not(:hover) {
        transition: 0.3s ease-out;
    }    
}

.view {
    background-color: $yellow;
    color: $white;

    &:hover {
        background-color: $white;
        color: $pink2;
        transition: 0.3s ease-in;
    }

    &:not(:hover) {
        transition: 0.3s ease-out;
    }
}

</style>