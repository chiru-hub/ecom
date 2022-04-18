<template>
  <div class="page-cart">
    <div class="colums is-multiline">
      <div class="colum is-12">
        <h1 class="title">Cart</h1>
      </div>
      <div class="column is-12 box">
        <table class="table is-fullwidth" v-if="cartTotalLength">
          <thead>
            <tr>
              <th>Product</th>
              <th>Price</th>
              <th>Quantity</th>
              <th>Total</th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <CartItem
              v-for="item in cart.items"
              :key="item.product.id"
              :initialItem="item"
            />
          </tbody>
        </table>
        <p v-else>You don't have any products in your cart...</p>
      </div>
      <div class="column is-12 box">
        <h2 class="subtitle">Summary</h2>
        <strong></strong>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import CartItem from "@/components/CartItem.vue";
export default {
  name: "Cart",
  components: {
    CartItem,
  },
  data() {
    return {
      cart: {
        items: [],
      },
    };
  },
  mounted() {
    this.cart = this.$store.state.cart;
    console.log(this.cart.items);
  },
  computed: {
    cartTotalLength() {
      return this.cart.items.reduce((acc, curVal) => {
        return (acc += curVal.quantity);
      }, 0);
    },
  },
};
</script>
