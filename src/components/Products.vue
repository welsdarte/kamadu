<template>
    <div class="products">
        <strong>{{product.title}}</strong>
        <p>{{product.description}}</p>
        <strong>Fiyat: {{product.price}} | Adet: {{product.count}}</strong>
        <br>
        <button @click='addToCart(product)' id='sepeteEkle'>Sepete Ekle</button>
    </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    props:['product'],
    methods:{
        addToCart(product){
            this.$emit('addToCart',product);
        }
    }
})
</script>
<style>
    .products{
        border: 2px dashed #666;
        padding: 5px 10px;
        width: 300px;
        margin-bottom: 7px;
    }
    .products:hover{
        border: 2px solid tomato;
    }
</style>