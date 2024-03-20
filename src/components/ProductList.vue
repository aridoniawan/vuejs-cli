<template>
    <div>
        <transition-group  name="fade" tag="div" @beforeEnter="before" @enter="enter" leave="leave">
        <div class="row mb-3 align-items-center" v-for="(item, index) in showItems" :key="item.id" :data-index="index">
        <div class="col-1">
            <button class="btn btn-info" @click="$emit('add-item', item)">+</button>
        </div>
        <!-- <div class="col-1" v-if="cart.length > 0">
            <span class="btn btn-outline-success">{{cart.length}}</span>
        </div> -->
        <!-- <div class="col-1">
            <button class="btn btn-danger" @click="delItem(index)">-</button>
        </div> -->
        <div class="col-sm-4">
            <img :src="item.image" :alt="item.name" class="img-fluid">
        </div>
        <div class="col">
            <h1>{{item.name}}</h1>
            <p>{{item.description}}</p>
            <div class="h5 float-right">
                <PriceComponent :value="Number(item.price)"></PriceComponent>
            </div>
        </div>
    </div>
    </transition-group>
    </div>
</template>

<script>

import PriceComponent from "./PriceComponent.vue";

export default {
    name: "product-list",
    components: {
        PriceComponent
    },
    props: ["products", "maximum"],
    computed: {
        showItems: function(){
            let max = this.maximum;
            return this.products.filter(function(item){
                return item.price <= max;
            });
        }
    },
    methods: {
        before: function(el){
            el.className= 'd-none';
        },
        enter: function(el){
            var delay= el.dataset.index * 100;
            setTimeout(function(){
                el.className = 'row d-flex mb-3 align-items-center animated fadeInLeft'
            }, delay)
   
        }, 
        leave: function(el){
            var delay= el.dataset.index * 100;
            setTimeout(function(){
                el.className = 'row d-flex mb-3 align-items-center animated fadeOutRight'
            }, delay)
        },
    },
    
}
</script>