<template>
  <div id="app" class="container mt-5">
    <h1 class="animate__fadeInLeft">IDShops</h1>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
    <PriceComponent :value="4.23"></PriceComponent>
    <product-list :products="products" :maximum="maximum"></product-list>
  </div>
</template>

<script>
// import {FontAwesomeIcon} from '@fortawesome/vue-fontawesome';
import ProductList from "./components/ProductList.vue";

export default {
  name: 'App',
  data: function(){
    return{
      maximum: 50,
      products: []
    }
  },
  components: {
    // FontAwesomeIcon,
    ProductList
  },
  mounted:function()
    {
        fetch('https://hplussport.com/api/products/order/price')
        .then(response => response.json())
        .then(data=>{
            this.products = data;
        });
    },
}
</script>
<!-- ./components/PriceComponent.vue -->
