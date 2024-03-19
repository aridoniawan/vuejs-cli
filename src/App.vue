<template>
  <div id="app" class="container mt-5">
    <h1 class="animate__fadeInLeft">IDShops</h1>
    <P class="animate__animated animate__fadeInLeft">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odio a quod, excepturi, recusandae inventore facilis, eius ut libero ipsa quibusdam porro? Voluptatum dicta minima, rem sint iusto sit. Nesciunt dolores sint dignissimos hic ab dolor laborum repellat, 
      adipisci inventore esse id repudiandae odio impedit itaque, necessitatibus corporis ad iure. Id.
    </P>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
    <PriceComponent :value="4.23"></PriceComponent>
  </div>
</template>

<script>
import {FontAwesomeIcon} from '@fortawesome/vue-fontawesome';
import PriceComponent from "./components/PriceComponent.vue";

export default {
  name: 'App',
  components: {
    FontAwesomeIcon,
    PriceComponent,
  }
}
</script>
./components/PriceComponent.vue
