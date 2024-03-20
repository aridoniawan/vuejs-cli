<template>
    <div>
        <h1 class="animate__animated animate__fadeInLeft">IDShops</h1>
        <navbarComponent :cart="cart" :cartQty="cartQty" :cartTotal="cartTotal" @toggle-slide="toggleSlider" @delete-item="deleteItem"></navbarComponent>
        <!-- <font-awesome-icon icon="shopping-cart"></font-awesome-icon> -->
        <!-- <PriceComponent :value="4.23"></PriceComponent> -->
        <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum"></price-slider>
        <!-- <PriceSlider :sliderStatus="sliderStatus" :maximum.sync="maximum"></PriceSlider> -->
        <product-list :products="products" :maximum="maximum" @add-item="addItem"></product-list>
    </div>
</template>

<script>
import NavbarComponent from './NavbarComponent.vue';
// import PriceComponent from './PriceComponent.vue';
import PriceSlider from './PriceSlider.vue';
import ProductList from './ProductList.vue';

export default {
    name: "ProductComponent",
    props: [
        "products",
        "maximum",
        "cart",
        "cartQty",
        "cartTotal",
        "sliderStatus",
        "sliderState"
    ],
    components: {
        NavbarComponent, PriceSlider, ProductList
    },
    methods:{
        toggleSlider: function(){
            this.$emit('toggle');
        },
        addItem: function(item){
            this.$emit('add', item);
        },
        deleteItem: function(index){
            this.$emit('delete', index);
        },
    }
}
</script>