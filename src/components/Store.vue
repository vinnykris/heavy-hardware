<template>
  <div id="app">
    <div v-for="product in products" :key="product">
        <!-- <div>{{product.title}}</div> -->
        <!-- <div class="product-image"> -->
            <img class="product-image" :src="product.images[0].src" @click="showProductDetail(product)"/>
        <!-- </div> -->
        <div v-if="product.show_detail">
            <product-detail :product="product"/>
        </div>
    </div>
    
  </div>
</template>

<script>

import Client from 'shopify-buy'
import Product from './Product.vue'
import Vue from 'vue'

export default {
  name: 'Store',
  data() {
      return {
        //   filteredProducts: [],
          products: [],
          //showDetail: false,
      }
  },

  components: {
      'product-detail': Product,
  },

  mounted: function () {// When the app is ready load the products
      this.loadProducts();
    },
    methods: {
        enumerate: function (v) { var k = 0; return v.map(function (e) { e._idx = k++ }) },
        processProducts: function () {
            this.products.map(function (e) {
                Vue.set(e, 'show_detail', false);
            });
        },
        loadProducts: function() {
            //this.filteredProducts = this.products;

        },
        showProductDetail: function(product) {
            for (var i = 0; i < this.products.length; i++) {
                if (this.products[i].id != product.id) {
                    this.products[i].show_detail = false;
                }
            }
            product.show_detail = !product.show_detail;
            console.log(product.title);
        }
    },
    created: function() {
        var client = Client.buildClient({
            domain: 'heavy-hardware.myshopify.com',
            storefrontAccessToken: '89e44554086e25c2a6834ccd9c5bed3e' // previously apiKey, now deprecated
        })
        // Fetch all products in your shop
        client.product.fetchAll().then((products) => {
            // Do something with the products
            this.products = products;
            console.log(products);
            this.loadProducts();
            this.processProducts();
        }) 
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.product-image {
    height: 100px;
    width: 100px;
}
</style>
