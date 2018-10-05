<template>
    <div class="container">
        <component :is="selectedComponent"></component>
    </div>
</template>
<script>
    import Card from './Card'

    export default {
        data() {
            return {
                selectedComponent: Card
            }
        },
        components: {
            Card: 'Card'
        }
    }
</script>
<style>
    .card{
        width: 180px;
        height: 232px;
        border: 2px solid #5C9C00;
        border-radius: 5px;
        transition: box-shadow .2s;
        margin: 20px;
        display: inline-flex;

    }

    .card:hover{
        box-shadow: 0px 5px 10px 10px #7cbb00b0;
        transition: box-shadow .2s;
    }
    .selectedCardClass{
        box-shadow: 0px 5px 10px 10px #00bbaab0 !important;
        border: 2px solid #009c8e !important;
        transition: width .2s;
    }
    .imgStyle{
        border-radius: 5px;
    }
    .bgImage{
        background-image: url("/src/assets/vue-js-egitim-background.jpg");
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
    }
    .center{
        text-align: center;
    }
    .rotate-enter{}
    .rotate-enter-active{
        animation: rotate ease-in-out 6s forwards;
    }
    .rotate-leave{}
    .rotate-leave-active{} //deattached işlemi yok

    .showCard-enter{
        animation: turn-in ease-in-out 3s forwards;
    }
    .showCard-enter-active{
        animation: turn-in ease-in-out 3s forwards;
    }
    .showCard-leave{
        animation: turn-out ease-in-out 3s forwards;
    }
    .showCard-leave-active{
        animation: turn-out ease-in-out 3s forwards;
    }
    @keyframes rotate {
        from{
            transform: rotateY(0deg);
        }
        to{
            transform: rotateY(360deg);
        }
    }
    @keyframes turn-in {
        from{
            transform: rotateY(90deg);
        }
        to{
            transform: rotateY(0deg);
        }

    }
    @keyframes turn-out {
        from{
            transform: rotateY(0deg);
        }
        to{
            transform: rotateY(90deg);
        }

    }
</style>
