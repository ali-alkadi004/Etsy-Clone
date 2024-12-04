<template>
  <div class="layout">
    <!-- Sidebar -->
    <aside class="sidebar">
      <button @click="showComponent('Headbar')">Headbar</button>
      <button @click="showComponent('Footer')">Footer</button>
      <button @click="showComponent('Help')">Help</button>
      <button @click="showComponent('SpecialShop')">Special Shop</button>
      <button @click="showComponent('HolidayHub')">Holiday Hub</button>
      <button @click="showComponent('Saving')">Saving</button>
      <button @click="showComponent('Registry')">Registry</button>
      <button @click="showComponent('FeaturedCategories')">Featured Categories</button>
      <button @click="showComponent('Jewelry')">Jewelry</button>
      <button @click="showComponent('ElectronicsFilter')">Electronics Filter</button>
      <button @click="showComponent('Filters')">Filters</button>
      <button @click="showComponent('MyCart')">My Cart</button>
      <button @click="showComponent('SignIn')">Sign In</button>
      <button @click="showComponent('FavoriteItems')">Favorite Items</button>
    </aside>

    <!-- Main Content -->
    <main class="content">
      <component
        :is="currentComponent"
        @add-to-cart="handleAddToCart"
        :cart-items="cartItems"
      />
    </main>
  </div>
</template>

<script>
import Headbar from "~/components/Headbar.vue";
import Footer from "~/components/Footer.vue";
import Help from "~/components/Help.vue";
import SpecialShop from "~/components/SpecialShop.vue";
import HolidayHub from "~/components/HolidayHub.vue";
import Saving from "~/components/Saving.vue";
import Registry from "~/components/Registry.vue";
import FeaturedCategories from "~/components/FeaturedCategories.vue";
import Jewelry from "~/components/Jewelry.vue";
import ElectronicsFilter from "~/components/ElectronicsFilter.vue";
import Filters from "~/components/Filters.vue";
import MyCart from "~/components/MyCart.vue";
import SignIn from "~/components/SignIn.vue";
import FavoriteItems from "~/components/FavoriteItems.vue";

export default {
  name: "DefaultLayout",
  components: {
    Headbar,
    Footer,
    Help,
    SpecialShop,
    HolidayHub,
    Saving,
    Registry,
    FeaturedCategories,
    Jewelry,
    ElectronicsFilter,
    Filters,
    MyCart,
    SignIn,
    FavoriteItems,
  },
  data() {
    return {
      currentComponent: null, // Default component is null to ensure nothing renders initially
      cartItems: [], // Stores items added to the cart
    };
  },
  methods: {
    showComponent(componentName) {
      this.currentComponent = componentName; // Dynamically switch components based on user click
    },
    handleAddToCart(item) {
      const existingItem = this.cartItems.find(
        (cartItem) => cartItem.name === item.name
      );
      if (existingItem) {
        existingItem.quantity++; // Increment quantity if item already exists in cart
      } else {
        this.cartItems.push({ ...item, quantity: 1 }); // Add new item to cart
      }
    },
  },
};
</script>

<style scoped>
/* Layout */
.layout {
  display: flex;
  height: 100vh;
}

/* Sidebar */
.sidebar {
  width: 200px;
  background-color: #f4f4f4;
  padding: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  border-right: 1px solid #ddd;
}

.sidebar button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  font-size: 14px;
  text-align: left;
  cursor: pointer;
}

.sidebar button:hover {
  background-color: #0056b3;
}

/* Content */
.content {
  flex: 1;
  padding: 20px;
}
</style>
