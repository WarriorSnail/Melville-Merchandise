<template>

<div id="app">
  <div class="product">


    <div class="product-image">
      <img alt="Vue logo" v-bind:src='image'><!-- div class linking to image variable in javascript code-->
    </div>
    
    <div class="product-info">
      <h1>{{ title }}</h1><!-- h1 with variable for title-->
      <p id="stock" v-if="inStock">In Stock</p><!-- if inStock is true this shows In Stock-->
      <p v-else>Out of Stock</p><!-- else it shows out of stock-->

      <ul>
        <li v-for="detail in details" :key="detail">{{detail}}</li><!-- for loop iterated through details array to give list-->
      </ul>
      <div v-for="(variant, index) in variants" 
          :key="variant.variantID"
          class="color-box"
          :style="{ backgroundColor: variant.variantColor}" 
          @mouseover="updateProduct(index)"> <!-- this uses the variantColour stored in variables to display coloured squares-->
      </div>

      <button v-on:click="add" 
      :disabled="!inStock"
      :class="{ disabledButton: !inStock }">Add to Cart</button><!-- button that enables when item in stock and calls add method when clicked-->
      
      <div class="cart">
        <p>Cart({{cart}})</p><!-- just a cart class that gets increased by the add method-->
      </div>
       
    </div>


  </div>
</div>
  </template>
  
  <script>
    export default {
  name: 'app',

  

  data() {
    return {
      brand: 'Melville Merchandise',//data method returns required variables
      product: "T-Shirts",
      selectedVariant: 0,
      details: ["High quality product", "Support your local producer", "Comes in 2 colours"],
      
      variants: [
        {
          varintID: 21,
          variantColor: "Red",
          vImage: require("D:/App3/hello/src/assets/red.jpg"),//an array of variants to pass on info based on which is picked
          vQuantity: 10
        },
        {
          variantID: 22,
          variantColor: "blue",
          vImage: require("D:/App3/hello/src/assets/blue.jpg"),
          vQuantity: 0
        }
      ],
      cart: 0
    }
    
    
  },
  methods: {
  add: function () {
    this.cart += 1  //method that adds 1 to cart
  },
  updateProduct: function (index) {//method that updates product variant when triggered
    this.selectedVariant=index
    console.log(index)
  }
  },
  computed: {
    title() {// computed method combines brand and product in one string
      return this.brand + ' ' + this.product
    },
    image() {
      return this.variants[this.selectedVariant].vImage//returns right image of selected variant
    },
    inStock() {
      return this.variants[this.selectedVariant].vQuantity//tells whether variant is in stock or not
    }
  }
}
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>/* styling only this component due to scoped attribute*/
  
  body {
    font-family: tahoma;
    color:#282828;
    margin: 0px;
  }
  .product {
    display: flex;
    flex-flow: wrap;
    padding-top: 5rem;
  }
  img {
    border: 1px solid #d8d8d8;
    width: 70%;
    margin: 40px;
    box-shadow: 0px .5px 1px #d8d8d8;
  }
  
  .product-image {
    width: 80%;
  }
  
  .product-image,
  .product-info {
    margin-top: 10px;
    width: 50%;
  }
  
  .color-box {
    width: 40px;
    height: 40px;
    margin-top: 5px;
  }
  
  .cart {
    margin-right: 25px;
    float: right;
    border: 1px solid #d8d8d8;
    padding: 5px 20px;
    background-color: rgb(255, 0, 0);
    color: white;
  }
  
  button {
    margin-top: 30px;
    border: none;
    background-color: rgb(255, 0, 0);
    color: white;
    height: 40px;
    width: 100px;
    font-size: 14px;
  } 
  
  .disabledButton {
    background-color: #d8d8d8;
  }
  
  .review-form {
    width: 400px;
    padding: 20px;
    margin: 40px;
    border: 1px solid #d8d8d8;
  }
  
  input {
    width: 100%;  
    height: 25px;
    margin-bottom: 20px;
  }
  
  textarea {
    width: 100%;
    height: 60px;
  }

  .tab {
    margin-left: 20px;
    cursor: pointer;
  }

  .activeTab {
    color: #16C0B0;
    text-decoration: underline;
  }
  </style>
  