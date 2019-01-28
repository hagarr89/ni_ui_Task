<template>
    <div class="products-comp">
        <product-comp v-for="product in products" :key="`product${product.id}`" :product="product"></product-comp>
    </div>
</template>
<script>
import productComp from './productComp'

export default {
    name:'products-comp',
    components:{
        productComp
    },
    data(){
        return{
            products:[
                {
                    id:1,
                    image:'product-home-chef.jpg',
                    logo:'logo-home-chef.svg',
                    checkList:[
                            {
                                id:1,
                                text:'$30 off your first order'
                            },
                             {
                                id:2,
                                text:'Healthy meals in 30 minutes'
                            },
                             {
                                id:3,
                                text:'Fresh ingredients, not frozen'
                            }
                    ]
                },
                {
                    id:2,
                     image:'product-home-chef.jpg',
                    logo:'logo-home-chef.svg',
                    checkList:[
                            {
                                id:1,
                                text:'$30 off your first order'
                            },
                             {
                                id:2,
                                text:'Healthy meals in 30 minutes'
                            },
                             {
                                id:3,
                                text:'Fresh ingredients, not frozen'
                            }
                    ]
                }
            ]
        }
    }

}
</script>
<style lang="scss">
@import '../styles/variables.scss';
@import '../styles/share.scss';
</style>
