<template>
  <div>
    <product-detail :product="product"></product-detail>
  </div>
</template>



<script>
import ProductDetail from '@/components/products/ProductDetail.vue'

export default{
    created(){
       const {name} = product;
       if(!name){
           this.$store.dispatch('productById', {
               productId: this.$route.params['id']
           });
       }
    },

    computed:{
        product(){
            return this.$store.getters.productById(this.$route.params['id'])
        }
    },

    components:{
        'product-detail': ProductDetail
    },
}
</script>
