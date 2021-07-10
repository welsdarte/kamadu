<template>
  <div class='container'>
    <!-- <comp></comp> -->
    <hr>
    <span id='back'>
      <div>
        <h3>Sepet</h3>
      <ul>
        <li  v-for='item in cartItems' :key="item.id">{{item.title}} {{item.countOnCart}} adet</li>
      </ul>
      </div>
      <products @addToCart='addToCart($event)' :product='product' v-for='product in productList' :key='product.id'></products>
    </span>
  </div>
  
</template>

<script lang="ts">
  import denemeComponent from "./components/denemeComponent.vue";
  import products from './components/Products.vue'
  import Vue from 'vue'
  export default Vue.extend({
    components:{
      // comp:denemeComponent,
      products
    },
    data(){
      return {
        productList:[
          {
            id:1,
            title:'MackBook Pro x asdf',
            price:100,
            count:10,
            description:'Aciklama 1',
            countOnCart:0
            
          },
          {
            id:2,
            title:'Iphone 12',
            price:50,
            count:200,
            description:'Aciklama 2',
            countOnCart:0
          },
          {
            id:3,
            title:'Keyboard',
            price:10,
            count:500,
            description:'Aciklama 3',
            countOnCart:0
          }
        ],
        cartItems:[]
      }
    },
    methods:{
      addToCart(event){
        if(this.cartItems.some(item => item.id === event.id)){
          let item=this.cartItems.find(item => item.id ===event.id);
          item.countOnCart++;
          item.count--;
        }
        else{
          this.cartItems.push(event);
          let obj=this.cartItems.find(item => item.id ===event.id);
          obj.countOnCart++;
          obj.count--;
        }
      }
    }
  });
</script>
<style>
  .container{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background-color:rgba(143,12,75,0.3);
    border:5px solid rgba(143,12,75,0.5) ;
    
  }
  #back{
    background-color: rgba(143,12,75,0.1);
    align-items: center;
    height: 100%;
    justify-content: center;
  }
</style>