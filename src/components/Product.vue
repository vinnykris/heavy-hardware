<template>
    <sweet-modal ref=modal>
      <div id="my-product0"></div>
      <div id="my-product1"></div>
      <div id="my-product2"></div>
      <div id="my-product3"></div>
      <div id="my-product4"></div>
    </sweet-modal>
</template>

<script>

import Client from 'shopify-buy'
import { SweetModal, SweetModalTab } from 'sweet-modal-vue'

export default {
  name: 'Product',
  props: ['product', 'index'],
    data() {
        return {
          componentKey: 0,
        }
    },

    components: {
        SweetModal,
        SweetModalTab,
    },
    methods: {
        open: function (index) {

            // EVENT LISTENER ATTEMPT
            this.$refs.modal.open();
            console.log('modal loaded');
            this.loadData();
            
        },
        loadData: function() {
          var client = Client.buildClient({
              domain: 'heavy-hardware.myshopify.com',
              storefrontAccessToken: '89e44554086e25c2a6834ccd9c5bed3e' // previously apiKey, now deprecated
          });

          var ui = ShopifyBuy.UI.init(client);
          console.log(this.product);
          ui.createComponent('product', {
              id: this.product.id,
              node: document.getElementById('my-product' + this.index)
          });
          this.$forceUpdate();
        },
        forceRerender() {
          this.componentKey += 1;
          console.log("force re-render called")
        },
    },
    created: function() {
        console.log("product component created");
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
    min-height: 15em;
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

.modal-fade-enter,
  .modal-fade-leave-active {
    opacity: 0;
  }

  .modal-fade-enter-active,
  .modal-fade-leave-active {
    transition: opacity .5s ease
  }

.btn-close {
    border: none;
    font-size: 20px;
    padding: 20px;
    cursor: pointer;
    font-weight: bold;
    color: #4AAE9B;
    background: transparent;
  }
</style>
