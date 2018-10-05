<template>

         <div class="card center ">
             <img class="imgStyle" :src=card.url alt="">
         </div>

</template>

<script>
    export default {
        name: "SecretCard",
        props:["card"],
        data(){

            return{
            }
        },
        created(){

        }
    }
</script>

<style scoped>

</style>