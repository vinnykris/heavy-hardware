<template>
    <div>
        <sweet-modal icon="success" ref="modal" title="New Modal">Success!
            <!-- <sweet-button slot="button">That's fine!</sweet-button> -->
        </sweet-modal>
    </div>
</template>

<script>

import Client from 'shopify-buy'
import { SweetModal, SweetModalTab } from 'sweet-modal-vue'

export default {
  name: 'Product',
  props: ['product'],
    data() {
        return {
            modalVisible: false,
        // //   filteredProducts: [],
        //   products: [],
        }
    },

    components: {
        SweetModal,
        SweetModalTab
    },
    methods: {
        open: function () {
            this.$refs.modal.open()
        },
        // show () {
        //     this.$modal.show('product-modal');
        // },
        // hide () {
        //     this.$modal.hide('product-modal');
        // }
        close() {
            this.$emit('close');
        },
    },
    created: function() {
        console.log("product component created");
        //this.show();
        // this.open();
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
