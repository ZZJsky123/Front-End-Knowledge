<template>
  <div>
    <div class="product">
      <router-link to="'/detail/' + product._id" class="product-link">
        <p class="product__name">产品名称: {{product.name}}</p>
        <p class="product__description">介绍: {{product.description}}</p>
        <p class="product__price">价格: {{product.price}}</p>
        <p class="product__manufacturer">生产产商: {{product.manufacturer}}</p>
        <img :src="product.image" alt="" class="product__image">
      </router-link>
    </div>
     <product-button :product="product"></product-button>
   </div>
</template>

<script>
import ProductButton from './ProductButton.vue'

export default{
    name:'product-item',
    props: ['product'],
    components: {
        'product-button': ProductButton
    }
}
</script>

<style scoped>
    .product {
    border-bottom: 1px solid black;
    }

    .product__image {
    width: 100px;
    height: 100px;
    }
</style>
