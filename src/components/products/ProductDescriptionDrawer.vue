<template>
    <div class="background" :class="{show: active}" @click="$emit('close-product-drawer')"></div>
    
    <div class="drawer" :class="{show: active}">
        <div class="drawer__close"  @click="$emit('close-product-drawer')">X</div>
        
        <div v-if="product" class=drawer__details>
            
            <h3 class="drawer__details__text">{{product.name}}</h3>
            <p class= "drawer__details__description">{{product.description}}</p>
            <h3 class="drawer__details__text">{{ product.price.toFixed(2)}}</h3>

            <div class="drawer__details__total" v-if="productTotal">
                <h3 class="drawer__details__text">In cart</h3>
                <h4 class="drawer__details__text">{{productTotal}}</h4>
            </div>
            <div class="drawer__details__button">
                <AwesomeButton :text="'Add'" @click="addToCart()"></AwesomeButton> 
                <AwesomeButton :text="'Remove'" @click="removeFromCart()"></AwesomeButton> 
            </div>
        </div>
    </div>
</template>

<script>



// import { computed } from 'vue';
import AwesomeButton from "../buttons/AwesomeButton.vue"

export default {
    props : 
    {
    product: {
        type: String,
        default: ""    
    },
    active: {
        type: Boolean,
        default: false,
    },
    
  },

  components: {
        AwesomeButton
    },
  computed: {
        productTotal(){
            return this.$store.getters.productQuantity(this.product);
        }
    },
  methods: {
        addToCart(){
            console.log("ggg")
            this.$store.commit('addToCart', this.product);
        },
        removeFromCart(){
            this.$store.commit('removeFromCart', this.product)
        }
    },
//   setup() {
//       const productTotal = computed(() => `this.{$store.getters.productQuantity(this.product)}`)

//       return{ productTotal }
//   }

}
</script>


<style lang="scss" >
.background {
    width: 100%;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
    background-color: rgba(120,120,120, 0.6);
    z-index: 100; // refactor create teleport
    display: none;
    transform: display .5s;
    &.show {
        display: block;
    }
}
.drawer {
    width: 95vw;
    height: 100vh;
    background-color:#fff;
    position: fixed;
    top:0;
    left: -105vw;
    transition: left .5s;
    z-index: 102;
    overflow-y: scroll;
    &.show {
        left:0;
    }
    &__close {
        font-size: 1.5rem;
        padding: 0.2rem;
        border-radius: 0.2rem;
        right: 0.7rem;
        border: 0.1rem solid #808080;
        color: #808080;
        width: 0.95rem;
        float: right;
        cursor: pointer;
        &:hover{
            background-color: lightgrey;
        }
    }
    &__details{
        
        display: flex;
        align-items: center;
        flex-direction: column;
        &__description{
            margin-top: .8rem;
            padding: 1.6rem;
            line-height: 1.5rem;
        }
        &__text{
            margin-top: 0.5rem;
        }
        &__button{
            margin-top: 0.8rem;
            width: 15rem;
            display: flex;
            justify-content:space-around;
            button {
                width: 5rem;
                }
            }
            
        }

    }

@media (min-width: 500px){
    .drawer{
    width: 450px;
    }
}
</style>