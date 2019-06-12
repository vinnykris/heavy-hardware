<template>
  <div id="app"> 
  </div>
</template>

<script>

import Client from 'shopify-buy'

import { SweetModal, SweetModalTab } from 'sweet-modal-vue'
import Vue from 'vue'

export default {
  name: 'Store',
  data() {
      return {
        products: [],
      }
  },

  components: {
      SweetModal,
      SweetModalTab,
  },

  mounted: function () {// When the app is ready load the products
      this.processProducts();
    },
    methods: {
        enumerate: function (v) { var k = 0; return v.map(function (e) { e._idx = k++ }) },
        processProducts: function () {
            this.enumerate(this.products);
        },
        showProductDetail: function(product, index) {
            this.$refs.details[index].open(index);
            console.log(product.title);
        },
        setupComponents: function () {
          var client = Client.buildClient({
              domain: 'heavy-hardware.myshopify.com',
              storefrontAccessToken: '89e44554086e25c2a6834ccd9c5bed3e' // previously apiKey, now deprecated
          });

          var ui = ShopifyBuy.UI.init(client);
          for (var i = 0; i < this.products.length; i++){
            var product = this.products[i];
            ui.createComponent('product', {
              id: product.id,
              options: {
                product: {
                  buttonDestination: 'modal',
                  isButton: true,
                  iframe: true,
                  width: 'false',
                  contents: {
                    // image: true,
                    img: true,
                    title: false,
                    variantTitle: false,
                    price: false,
                    options: false,
                    quantity: false, // determines whether to show any quantity inputs at all
                    quantityIncrement: false, // button to increase quantity
                    quantityDecrement: false, // button to decrease quantity
                    quantityInput: false, // input field to directly set quantity
                    button: false,
                    description: false,
                  },
                },
                modal: {
                  styles: {
                    button: {
                      'background-color': 'black',
                    }
                  }
                },
                modalProduct: {
                  contents: {
                    img: false,
                    imgWithCarousel: true,
                  },
                },
                toggle: {
                  styles: {
                    toggle: {
                      'background-color': 'black',
                    }
                  }
                },
                cart: {
                  startOpen: false,
                  iframe: true,
                  styles: {
                    button: {
                      'background-color': 'black',
                    }
                  }
                }
              }
            });
          }
          
        }
    },
    created: function() {
      let productData = require('./data/products.json');
      // console.log(productData.products);
      this.products = productData.products;
      this.setupComponents();
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

.img {
    height: 200px;
    width: 200px;
}
</style>
