<template>
  <div class="container">
    <ProductDescriptionDrawer
      :product="product"
      :active="product_drawer"
    />
    <div class="container__product">
      <ProductSummaryCard
      v-for="product in items"
      :key="product.id"
      :product="product"
      v-on:view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js'
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue'
import ProductDescriptionDrawer from '../components/products/ProductDescriptionDrawer.vue'
import { ref } from 'vue'


export default {
  name: 'Home',
  
  components: {
    ProductSummaryCard,
    ProductDescriptionDrawer
// },
//  data (){
//    return {
//      items: items
//    }
    
 },
 setup() {

      const product_drawer = ref(false);
      
      function viewProduct(product){
        this.product = product;
        console.log(product)
      }

      return {items,viewProduct, product_drawer}
    },
}
</script>
<style lang="scss">
.container__product{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>