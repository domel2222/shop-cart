<template>
    <div class="card">
        <h3>{{product.name}}</h3>

        <h5 class="card__price">Price: ${{ product.price.toFixed(2) }}</h5>
        <p class="card__description">Description: {{ product.description.substring(0, 150) }}</p>
        <p class="card__text--muted"> {{ product.category }}</p>
        
        <div class="card__button">
        <AwesomeButton :text="'View'" @click="$emit('view-product', product)"></AwesomeButton> 
        <AwesomeButton :text="'Lalala'"></AwesomeButton> 
        
        </div>
    </div>
</template>


<script>

import AwesomeButton from "../buttons/AwesomeButton.vue"


export default {
    props : {
        product: {
            type: String,
            default: '',
        },
    },
    components: {
    AwesomeButton
  }
}
</script>

<style lang="scss">
.card {
    width: 100%;
    margin: 10%;
    padding: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 5px;
    background-color: #fff;
    box-shadow: 0 0 5px #362828;
    &__price {
        margin: .8rem .8rem ;
        color: #b19f99;
    }
    &__dedcription {
        margin: 20px 20px ;
        font-size: .85rem;
    }
    &__text{
        &--muted {
            margin: 20px 20px ;
            color: #b19f9f;
        }
    }
    &__button{
        width: 12rem;
    display: flex;
    justify-content:space-around;
    }

}

@media (min-width: 500px) {
    .card {
        width: 21rem;
        margin: .8rem;
    }
}
</style>