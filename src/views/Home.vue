<template>
  <div class="container">
    <ProductDescriptionDrawer
      :product="product"
      :active="productDrawer"
      v-on:close-product-drawer="closeProductDrawer()"
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
},
//  data (){
//    return {
//      items: items,
//      product: null,
//      active: {
//        productDrawer: false
//      }
//    }
//  },
//  methods: {
//    viewProduct(product){
//      this.product = product,
//      this.active.productDrawer = true,
//      console.log(product);
//    }
//  },
    
 
 setup() {
      // console.log(items);
      const productDrawer = ref(false);
      const product = ref(null);
      function viewProduct(product){
        this.product = product;
        productDrawer.value = true;
      }

      function closeProductDrawer(){
        productDrawer.value = false;
      }
      return {viewProduct, productDrawer, product, items, closeProductDrawer}
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