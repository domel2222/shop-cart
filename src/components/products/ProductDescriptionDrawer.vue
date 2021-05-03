<template>
    <div class="background" :class="{show: active}" @click="$emit('close-product-drawer')"></div>
        
    <div class="drawer" :class="{show: active}">
        <div class="drawer__close"  @click="$emit('close-product-drawer')">X</div>
        
        <div v-if="product" class=drawer__details>
            
            <h3 class="drawer__details__text">{{product.name}}</h3>
            <p class= "drawer__details__description">{{product.description}}</p>
            <h3 class="drawer__details__text">{{ product.price.toFixed(2)}}</h3>

            <div class="drawer__details__total" v-if="productTotal">
                <h3>In cart</h3>
                <h4>{{productTotal}}</h4>
            </div>
            <div class="drawer__details__button">
                <button>Remove</button>
                <button>Add</button>
                 
                <!-- <AwesomeButton :text="'Add'">DUPA</AwesomeButton> 
                <AwesomeButton :text="'Remove'">DUPA</AwesomeButton>  -->
            </div>
        </div>
    </div>
</template>

<script>



import { computed } from 'vue';
// import ButtonSuper from "../buttons/ButtonSuper.vue"

export default {

    name: "ProductDescriptionDrawer",
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
    // components: {
    //     ButtonSuper
    // },
  },
//   computed: {
//         productTotal(){
//             return 56;
//         }
//     },
  setup() {
      const productTotal = computed(() => 56)

      return{productTotal}
  }

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
    z-index: 100;
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
        justify-content: center;
        flex-direction: column;
        &__description{
            padding: 1.6rem;
            line-height: 1.5rem;
        }
        &__button{
        display: flex;
        justify-content:space-around;
        }

    }
}
@media (min-width: 500px){
    .drawer{
    width: 450px;
    }
}
</style>