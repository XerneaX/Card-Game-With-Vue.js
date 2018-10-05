<template>
    <div>
        <div >
            <transition-group name="rotate" appear >
                <div class="card " v-for="card in cards" :key="card.url" @click="choseCard(card)"
                     :class="{'selectedCardClass': chosenCard.id === card.id}" >
                    <img class="imgStyle" :src=card.url alt="">
                </div>
            </transition-group>

        </div>
        <hr>
        <div class="center">

                <transition name="showCard" mode="out-in" >

                    <component @click.native="turnCard" :is="selectedComponent" :card="secretCard"
                               :class="{'selectedCardClass': isClicked }">
                       <p>GGG</p>
                    </component>

                </transition>


        </div>

    </div>

</template>

<script>
    import cardBack from './cardBack';
    import secretCard from './SecretCard'
    export default {
        name: "Card",
        components:{
            cardBack: 'cardBack',
            secretCard: 'secretCard'
        },
        data(){
            return{
                cards:[
                    {id:1, url:'/src/assets/card-1.jpg', component:"secretCard"},
                    {id:2, url:"/src/assets/card-2.jpg", component:"secretCard"},
                    {id:3, url:"/src/assets/card-3.jpg", component:"secretCard"},
                    {id:4, url:"/src/assets/card-4.jpg", component:"secretCard"},
                    {id:5, url:"/src/assets/card-5.jpg", component:"secretCard"}
                ],
                chosenCard: {},
                secretCard: {},
                isClicked: false,
                selectedComponent: cardBack

            }
        },
        created(){
            this.secretCard = this.cards[Math.round(Math.random()*4)];
        },
        methods:{
            choseCard(card){debugger;
                this.chosenCard = card;
                //this.selectedComponent = secretCard;
            },
            turnCard(){debugger;
                if(this.chosenCard.id){
                    this.selectedComponent = secretCard;
                    this.isClicked = true;
                }
                else
                    alert("Lütfen Bir Kart Seçiniz");

            }
        }
    }
</script>

<style scoped>
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