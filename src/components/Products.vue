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
        border: 2px solid rgba(143,12,75,1);
    }
    #sepeteEkle{
        background-color: rgba(143,12,75,0.5);
        border: 2px solid rgba(143,12,75,1);
        color:rgb(241, 229, 235);
    }
    #sepeteEkle:hover{
        background-color: rgba(143,12,75,0.8);
    }
    #sepeteEkle:active{
        background-color: rgba(143,12,75,1);
    }
</style>