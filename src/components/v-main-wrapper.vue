<template>
    <div class="v-main-wrapper">
        <p> {{title}} </p>
        <v-catalog />
        <v-cart 
            v-if="CART.length"
            :cart_data="CART"
        
        
        />
    </div>
    
</template>

<script>
    import vCatalog from './v-catalog'
    import vCart from './v-cart'
    import {mapGetters} from 'vuex'


    export default {
        name: "v-main-wrapper",
        components:{
            vCatalog,
            vCart
        },

        
        props:{},
        data(){
            return{
                title: 'Main W!'
            }
        },
        computed:{
            ...mapGetters([
                'CART'
            ])
        },
        methods:{

        },
        watch:{},
        mounted(){
            console.log('Hey!')
        }

        
    }
</script>

<style>
    .main-wrapper{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        max-width: 900px;
        font-size: 20px;
        margin: 0;
    }
</style>