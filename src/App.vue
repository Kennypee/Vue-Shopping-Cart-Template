<template>
<div class="container">
  <div class="row">
    <div class="col-md-7">
      <div class="row">
        <div :key="product.id" class="col-md-6" v-for="product in products">
          <product :isAddedToCart="isAddedToCart(product)" v-on:add-to-cart="addToCart(product)" :product="product" />
        </div>
      </div>
    </div>
    <div class="col-md-5 my-5">
      <cart v-on:pay="PayNow()" v-on:remove-item="removeFromCart($event)" :items="cart"/>
      <!-- We must use the built-in $event variable to receive the event emitted from the child component -->
    </div>
  </div>
</div>
</template>

<script>
 import products from '@/products.json'
 import Product from '@/components/Product.vue'
 import Cart from '@/components/Cart.vue'

export default {
  name: 'app',

  components:{
    Product,
    Cart
  },

  methods:{
    addToCart(product){
      this.cart.push(product)
    },
    isAddedToCart(product){
      const item = this.cart.find(item => item.id === product.id)
      if(item){
        return true
      }else return false
    },
    removeFromCart(item){
      
       this.cart = this.cart.filter(clickedItem => clickedItem !== item)
    },
    PayNow(){
      this.cart = []
      alert("Successfully placed your order !")
    }
  },

  data(){
    return{
      products,
      cart:[]
    }
  }
 
}
</script>

<style>
body{
  background: #E7f7f9;
}
</style>
