<template>
  <div id="app" class="container mt-5">
    <h1 class="animate__fadeInLeft">IDShops</h1>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
    <PriceComponent :value="4.23"></PriceComponent>
    <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum"></price-slider>
    <!-- <PriceSlider :sliderStatus="sliderStatus" :maximum.sync="maximum"></PriceSlider> -->
    <product-list :products="products" :maximum="maximum" @add="addItem"></product-list>
  </div>
</template>

<script>
// import {FontAwesomeIcon} from '@fortawesome/vue-fontawesome';
import PriceSlider from "./components/PriceSlider.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: 'App',
  data: function(){
    return{
      maximum: 50,
      products: [],
      cart: [],
      sliderStatus: true
    }
  },
  components: {
    // FontAwesomeIcon,
    PriceSlider,
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
  methods:{
    addItem: function(product){
            let productIndex;
            let productExist = this.cart.filter(function(item, index){
                if(item.product.id == Number(product.id)){
                    productIndex = index;
                    return true;
                }else{
                    return false;
                }
            });

            if(productExist.length){
                this.cart[productIndex].qty++
            }else{
                this.cart.push({product: product, qty:1})
            }
        }
  }
}
</script>
<!-- ./components/PriceComponent.vue -->
