<script>

    export default {

    name: "HeaderComponent",

    props: {

        links: Array,
        
    },

    data() {
        return {
            counter: 0
        }
    },
    methods: {
        scrollRight() {
            if(this.counter < 2) {
                this.counter ++
            } else {
                this.counter = 0
            }
        },
        scrollLeft() {
            if (this.counter >= 1) {
                this.counter--
            } else {
                this.counter = 2
            }
        },
    }
}
</script>


<template>

    <div class="header">
        <div class="background-red d-flex justify-content-center">
            <nav class="nav-bar container-fluid d-flex align-items-center justify-content-between">
                <img src="../../public/img/theme_eduprime_logo.png" alt="EduPrime" class="logo">
                <div class="d-flex align-items-end">
                    <ul class="d-flex">
                        <li v-for="(link, index) in links" :key="index" class="me-5 d-flex position-relative" @mouseover="link.hover = true" @mouseleave="link.hover = false">
                            <a :href="link.url" :class="{ 'active': link.current }">{{ link.title }}
                                <span v-if="link.arrow" :class="{ 'active': link.current }"><i class="fa-solid fa-sort-down"></i></span>
                            </a>
                            <Transition>
                                <div v-if="link.hover && link.pippo">
                                    <ul class="ul-dropdown position-absolute">
                                        <li v-for="(dropdown, index) in link.linksDropdown" :key="index">
                                            <a href="#nogo">{{ dropdown.text }}</a>
                                        </li>
                                    </ul>
                                </div>
                            </Transition>
                        </li>
                    </ul>
                    <a href="#">
                        <span class="view button text-uppercase">view courses</span>
                    </a>
                </div>
            </nav>
            <Transition>
                <div class="box-slider" v-if="counter == 0">
                    <div class="slider-1"></div>
                </div>
                <div class="box-slider" v-else-if="counter == 1">
                    <div class="slider-2"></div>
                </div>
                <div class="box-slider" v-else-if="counter == 2">
                    <div class="slider-3"></div>
                </div>
            </Transition>
            <div class="right">
                <span @click="scrollRight"><i class="fa-solid fa-angle-right"></i></span>
            </div>
            <div class="left">
                <span @click="scrollLeft"><i class="fa-solid fa-angle-left"></i></span>
            </div>
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
    transition: all 0.3s ease-in-out;

    &:hover {
        color: $yellow;
    }
}

span {
    position: relative;
    margin-left: 5px;
    bottom: 3px;
    font-size: 12px;
    cursor: pointer;
}


.button {
    @include button-general;
}


/* SPECIFICHE */

.header {
    height: 700px;
    position: relative;

    .background-red {
        background-color: $pink2;
        height: inherit;
        position: relative;

        .nav-bar {
            position: absolute;
            top: 0;
            padding: 30px 50px;
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
    transition: all 0.3s ease-in-out;

    &:hover {
        background-color: $yellow;
        color: $white;
    }
}

.btn-courses {
    background-color: $yellow;
    color: $white;
    transition: all 0.3s ease-in-out;

    &:hover {
        background-color: $white;
        color: $pink2;
    }
}

.view {
    background-color: $yellow;
    color: $white;
    transition: all 0.3s ease-in-out;

    &:hover {
        background-color: $white;
        color: $pink2;
    }
}

li:hover {
    color: $yellow;
}

/* SLIDER */

.right {
        position: absolute;
        top: 50%;
        left: 98%;
    }
.left {
    position: absolute;
    top: 50%;
    right: 98%;
}
.right, .left {
    font-size: 50px;
    cursor: pointer;
    color: $white;
}
.box-slider {
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: -1;
    
}
.slider-1 {
    background-image: url('../../public/img/theme_slider2_bg-1.jpg');
    background-size: cover;
    width: 100%;
    height: 100%;
}
.slider-2 {
    background-image: url('../../public/img/theme_slider3_bg-1.jpg');
    background-size: cover;
    width: 100%;
    height: 100%;
}
.slider-3 {
    background-image: url('../../public/img/theme_slider1_bg-1.jpg');
    background-size: cover;
    width: 100%;
    height: 100%;
}

.v-enter-active, .v-leave-active {
    transition: opacity 0.7s ease-in-out;
}
.v-enter-from,
.v-leave-to {
    opacity: 0;
}
.v-enter-to,
.v-leave-from {
    opacity: 1;
}

.ul-dropdown {
            background: $white;
            width: 200px;
            top: 80px;
            padding: 15px;
            left: -17px;
            border-radius: 10px;

            li {
                padding: 10px 13px;
            }

            li a {
                color: $black;
                font-size: 15px;
                &:hover {
                    color: $pink;
                }
            }    
        }

</style>