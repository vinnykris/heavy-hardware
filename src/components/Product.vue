<template>
    <div class="modal">
        <div class="modal-background">
            <div>{{product.title}}</div>
        </div>
    </div>
</template>

<script>

import Client from 'shopify-buy'

export default {
  name: 'Product',
  props: ['product'],
  data() {
      return {
        // //   filteredProducts: [],
        //   products: [],
      }
  },

  components: {

  },

  mounted: function () {// When the app is ready load the products
      //this.loadProducts();
    },
    methods: {
        loadProducts: function() {
            //this.filteredProducts = this.products;

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
            this.loadProducts();
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

.modal {
    z-index: 99;
    position: fixed;   
    top:50%;
    left:50%;
}
.modal-background {
    width: 30em;
    min-height: 1em;
    margin-top: -9em;
    margin-left: -15em;
    border: 2px solid #000000;
    background-color: #343434;
    color: #ffffff;
    opacity: 0.9;
}
.checkout {
    text-align: center;
    font-size: 30px;
}
.alignRight {
    text-align: right;
}
</style>
