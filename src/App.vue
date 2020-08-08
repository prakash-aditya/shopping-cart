<template>
  <!-- <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div> -->
  <ProductList />
</template>

<script lang="ts">
import{ Component, Prop, Vue } from "vue-property-decorator";
import ProductList from "./views/ProductList.vue";
import { HttpHandler } from "./data/httpHandler";
import { action } from './data/storeDecoraters';
import { Product } from './data/entities';

@Component({
  components: {
    ProductList
  }
})
export default class App extends Vue {
  private handler = new HttpHandler();

  constructor() {
    super();
    this.loadProducts(this.handler.loadProducts);
  }

  @action()
  loadProducts(task: () => Promise<Product[]>) {}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
