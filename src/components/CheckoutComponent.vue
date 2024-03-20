<template>
    <div>
        <h1>Chekcout</h1>
        <table class="table table-hover" v-if="cart.length">
            <caption class="text-right h3">
                <b>Total: </b>
                <PriceComponent class="d-block text-success font-weight-light" :value="Number(cartTotal)"></PriceComponent>
            </caption>
            <thead>
                <tr >
                    <th scope="col"></th>
                    <th scope="col">Item</th>
                    <th scope="col" class="text-center">Qty</th>
                    <th scope="col" class="text-right">Price</th>
                    <th scope="col" class="text-right">Sub-total</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in cart" :key="item.product.id">
                    <td class="text-center">
                        <div class="btn-group">
                            <button @click="$emit('add', item.product)" class="btn btn-info">+</button>
                            <button @click="$emit('delete', index)" class="btn btn-outline-info">-</button>
                        </div>
                    </td>
                    <th scope="row">{{ item.product.name }}</th>
                    <th class="text-center">{{ item.qty }}</th>
                    <th class="text-right">{{ Number(item.product.price) }}</th>
                    <th class="text-right">{{ Number(item.product.price * item.qty) }}</th>
                </tr>
            </tbody>
        </table>
        <router-link class="btn btn-sm btn-outline-info text-dark" to="/">Back to Shop</router-link>
    </div>
</template>

<script>

import PriceComponent from "./PriceComponent.vue";

export default {
    name: "checkoutComponent",
    props: ["cart", "cartTotal"],
    components: {
        PriceComponent
    }
}
</script>