<template>
    <article class="content" v-on:tab-changed="updateCarousel">
        <Tabs>
            <Tab name="My debit cards" :active="true">
                <div class="left-container">
                    <Carousel :perPage="1" :navigateTo="0" ref="carousel">
                        <slide v-for="info in cardInfo" :key="info.id" :data-index="info.id">
                            <Card :cardInfo="info" />
                        </slide>
                    </Carousel>
                    <CardAction />
                </div>
                <div class="right-container">
                    <CardAction />
                    <AccordionContainer />
                </div>
            </Tab>
            <Tab name="All company cards">
                <div class="left-container">
                    <Carousel :perPage="1" ref="carouselTab">
                        <slide v-for="info in cardInfo1" :key="info.id" :data-index="info.id">
                            <Card :cardInfo="info" />
                        </slide>
                    </Carousel>
                    <CardAction />
                </div>
                <div class="right-container">
                    <CardAction />
                    <AccordionContainer />
                </div>
            </Tab>
        </Tabs>
    </article>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';
import Tabs from './common/Tabs.vue';
import Tab from './common/Tab.vue';
import Card from './common/Card.vue';
import AccordionContainer from './AccodionContainer';
import CardAction from './CardAction';

export default {
    name: 'Conetnt',
    components: {
        Carousel,
        Slide,
        Tabs,
        Tab,
        Card,
        AccordionContainer,
        CardAction
    },
    data() {
        return {
            cardInfo: [
                {
                    id: "c-01",
                    name: "Mark Henry",
                    cardNumber: '1678980910102020',
                    cvv: '***',
                    validTill: '12/20'
                },
                {
                    id: "c-02",
                    name: "Mark Henry",
                    cardNumber: '1679980910102020',
                    cvv: '***',
                    validTill: '12/20'
                },
                {
                    id: "c-03",
                    name: "Mark Henry",
                    cardNumber: '1658980910102020',
                    cvv: '***',
                    validTill: '12/20'
                }
            ],
            cardInfo1: [
                {
                    id: "c-11",
                    name: "Divyaranjan Deviprasad",
                    cardNumber: '2404580910112021',
                    cvv: '***',
                    validTill: '12/20'
                },
                {
                    id: 'c-12',
                    name: "Divyaranjan Deviprasad",
                    cardNumber: '2404680915112021',
                    cvv: '***',
                    validTill: '12/20'
                },

            ]
        }
    },
    mounted() {
        setTimeout(this.$refs.carousel.computeCarouselWidth, 300)
    }
}
</script>

<style lang="scss">

.left-container {
    @include MediaQueries($desktop-and-above) {
        width: 50%;
    }
    @include MediaQueries($tablet-and-below) {
        position: sticky;
        top: 17.5rem;
    }
    .card-action {
        border-radius: 16px;
        margin-top: 2rem;
        @include MediaQueries($tablet-and-below) {
            display: none;
        }
    }
}

.right-container {
    margin: 1.5rem 0 0;
    background: $white;
    position: relative;
    z-index: $index2;
    border-radius: 16px 16px 0 0;
    @include MediaQueries($desktop-and-above) {
        width: 50%;
    }
}
@include MediaQueries($desktop-and-above) {
    .content {
        margin: 0 6rem 0 3rem;
    }
    .right-container {
        border-radius: 0;
        margin: 0 0 0 2rem;
        .card-action {
            display: none;
        }
    }
}

</style>