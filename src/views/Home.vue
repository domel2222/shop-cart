<template>
  <div class="container">
      <div class="container__product">
        <ProductSummaryCard
        v-for="product in items"
        :key="product.id"
        :product="product"
        />
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js'
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue'


export default {
  name: 'Home',
  
  components: {
    ProductSummaryCard
// },
//  data (){
//    return {
//      items: items
//    }
    
 },
 setup() {
      
      return {items}
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