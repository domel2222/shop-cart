<template>
  <div class="container">
      <div class="container__product">
        <ProductSummaryCard/>
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
},
 data (){
   return {
     items: items
   }
 }
}
</script>
<style lang="scss">
.container__product{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>