<script>

    export default {

        name: 'FirstMainComponent',

        props: {

            imgs: Array,
            items: Array

        },

        data() {
            return {

                text: 'law faculty', 

            }
        }
    }

</script>

<template>

    <div class="position-relative">
        <img src="../../public/img/home-background.png" class="wave-main">
        <div class="container">
            <section>
                <div class="d-flex pad">
                    <div class="description">
                        <img src="../../public/img/Books-icon.png" alt="Book Icon" class="book-icon">
                        <h2 class="display-5 fw-bold mb-5 mt-3">Thousand of courses for any type of student</h2>
                        <p>At EduPrime, it doesn&apos;t matter what domain you wish to pursue a career in. Here you can find a course that satisfies your needs whitin a click away and applies for a course in a matter of minutes. EduPrime is ranked as the most versatile university in the world, thanks to the number of courses it provides.</p>
                        <a href="#"><span class="browse button mt-3">Browse through courses</span></a>
                    </div>
                    <div class="w-50 mrg">
                        <img src="../../public/img/Graduation-Illustration.png" alt="Graduation image" class="graduation-img">
                    </div>
                </div>
            </section>
        </div>
        <section>
            <div class="d-flex align-items-center pad flex-column text-center">
                <h2 class="display-5 fw-bold mb-3">Faculties avaible at EduPrime</h2>
                <p class="mt-2">A single univerity whit a load of courses, tailored <br> to satisfy any student&apos;s needs.</p>
            </div>
            <div class="box-items mt-4">
                <div class="container d-flex text-center justify-content-center">
                    <div v-for="(img, index) in imgs" :key="index" class="box" :class="{ 'active': img.text == text }" @click="text = img.text">
                        <a href="#">
                            <img :src="img.img" :alt="img.text" class="img-faculties" :class="{ 'active': img.text == text }">
                            <p class="text-capitalize fw-bold faculties">{{img.text}}</p>
                        </a>
                    </div>
                </div>
            </div>
            <div v-for="(item, index) in items" :key="index" v-show="item.title == text">
                <div class="d-flex justify-content-center mt-5 pt-5">
                    <div class="box-img">
                        <img :src="item.img">
                    </div>
                    <div class="description-faculties" >
                        <h2 class="mb-4">{{ item.title }}</h2>
                        <p class="text">{{ item.text }}</p>
                        <a href="#"><span class="more button">Read More</span></a>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<style lang="scss" scoped>

@use '../assets/style/partials/variables' as *;
@use '../assets/style/partials/mixins' as *;


// GENERALI

.button {
    @include button-general;
}
.pad {
    padding-top: 150px;
}

.browse {
    background-color: $yellow;
    color: $white;
    font-size: 14px;
    font-weight: bold;
    transition: all 0.3s ease-in-out;

    &:hover {
        background-color: $red;
    }
}

.description {
    width: 60%;
}

.book-icon {
    width: 50px;
}

.graduation-img {
    width: 520px;
}

.mrg {
    margin-left: 90px;
}


.wave-main {
    position: absolute;
    top: 0;
    z-index: -1;
}

.box-items {
    box-shadow: 0px 0px 20px rgb(0 0 0 / 20%);
    
    .box {
        border-left: 2px solid $gray;
        position: relative;

        a {
            text-decoration: none;
        }

        .img-faculties {
            padding: 25px 70px;
        }

        .img-faculties.active {
            filter: invert(100%) sepia(0%) saturate(1%) hue-rotate(241deg) brightness(250%) contrast(101%);
        }

        .faculties {
            color: $pink2;
        }
    }

    .box.active {
        background-color: $pink;
        border: 0;
        
        p {
            color: $white;
        }

        a::after {
            position: absolute;
            top: 100%;
            left: 50%;
            margin-left: -15px;
            width: 0;
            height: 0;
            border: solid transparent;
            border-width: 15px;
            border-top-color: $pink;
            content: '';
            pointer-events: none;
        }
    }

    .box:last-child {
        border-right: 2px solid $gray;
    }
}

.description-faculties {
    width: 28.5%;
    margin-left: 100px;
    
    h2 {
        text-transform: capitalize;
    }

    .text {
        color: $gray-text;
        margin-bottom: 50px;
        margin-top: 40px;
    }
}

.more {
    background-color: $pink;
    color: $white;
    font-size: 14px;
    font-weight: bold;
    transition: all 0.3s ease-in-out;

    &:hover {
        background-color: $yellow;
    }
}

</style>