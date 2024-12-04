<template>
  <div class="layout">
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
    </aside>
    <main class="content">
      <component :is="currentComponent" v-if="currentComponent" />
    </main>
  </div>
</template>

<script>
import Headbar from '~/components/Headbar.vue';
import Footer from '~/components/Footer.vue';
import Help from '~/components/Help.vue';
import SpecialShop from '~/components/SpecialShop.vue';
import HolidayHub from '~/components/HolidayHub.vue';
import Saving from '~/components/Saving.vue';
import Registry from '~/components/Registry.vue';
import FeaturedCategories from '~/components/FeaturedCategories.vue';
import Jewelry from '~/components/Jewelry.vue';
import ElectronicsFilter from '~/components/ElectronicsFilter.vue';
import Filters from '~/components/Filters.vue';
import MyCart from '~/components/MyCart.vue';
import SignIn from '~/components/SignIn.vue';

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
  },
  data() {
    return {
      currentComponent: null,
    };
  },
  methods: {
    showComponent(componentName) {
      this.currentComponent = componentName;
    },
  },
};
</script>

<style scoped>
.layout {
  display: flex;
  height: 100vh;
}

.sidebar {
  width: 220px;
  background-color: #f4f4f4;
  padding: 20px;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
}

.sidebar button {
  display: block;
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  text-align: left;
}

.sidebar button:hover {
  background-color: #0056b3;
}

.content {
  flex: 1;
  padding: 20px;
  background-color: #ffffff;
  overflow-y: auto;
}
</style>
