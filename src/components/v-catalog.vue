<template>
    <div class="v-catalog">
        <h1>Catalog</h1>
    <div class="v-catalog__list"> 
        <v-catalog-item
            v-for ="product in PRODUCTS"
            :key="product.article"
            v-bind:product_data="product"
            @addToCart= "addToCart"
        />

        </div>    
        
    </div>
</template>

<script>
    import vCatalogItem from './v-catalog-item'
    import {mapActions, mapGetters} from 'vuex'
    export default {
        name: "v-catalog",
        components:{
            vCatalogItem,
        },
        props:{
            product_data: {
                type: Object,
                default(){
                    return{}
                }
            }
        },


        data(){
            return{}
        },


        computed:{
            ...mapGetters([
                'PRODUCTS'
            ]),
        },
        methods:{
            ...mapActions([
                'GET_PRODUCTS_FROM_API',
                'ADD_TO_CART'
            ]),
            addToCart(data){
                this.ADD_TO_CART(data)
            }
        },

        mounted() {
            this.GET_PRODUCTS_FROM_API()
            .then ((res) => {
                if(res.data){
                    console.log('AllaHu Akbar!!')
                }
            })
        }
    }
</script>

<style>
    .v-catalog__list{
    
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
    
        
    }
</style>