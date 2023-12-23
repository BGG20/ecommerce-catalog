<template>
  <div id="app">
    <ProductDisplay :product="currentProduct" @next-product="getNextProduct" />
  </div>
</template>

<script>
import axios from "axios";
import ProductDisplay from "@/components/ProductDisplay.vue";

const baseUrl = "https://fakestoreapi.com/products/";

export default {
  name: "App",
  components: {
    ProductDisplay,
  },
  data() {
    return {
      currentProductIndex: 1,
      currentProduct: {},
    };
  },
  methods: {
    async getApi(index) {
      try {
        const response = await axios.get(baseUrl + index);
        return response.data;
      } catch (error) {
        console.error(error);
        return null;
      }
    },
    async getNextProduct() {
      if (this.currentProductIndex <= 20) {
        const product = await this.getApi(this.currentProductIndex);
        if (product) {
          this.currentProduct = product;
          this.currentProductIndex++;
        }
      }
    },
  },
  mounted() {
    this.getNextProduct();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

button {
  margin-top: 10px;
  padding: 10px;
  background-color: #4caf50; /* Warna hijau tua */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>

<!-- <template>
  <div id="app">
    <h1>Hello, World!</h1>
  </div>
</template>

<script>
import axios from "axios";

const baseUrl = "https://fakestoreapi.com/products/";

export default {
  name: 'App',
  data() {
    return {};
  },
  methods: {
    async getApi() {
      try {
        const response = await axios.get(baseUrl);
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    },
  },
  mounted() {
    this.getApi();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
















 -->

<!-- <template>
  <div id="app">
    <h1>Hello, World!</h1>
    <ul>
      <li v-for="product in products" :key="product.id">
        {{ product.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

const baseUrl = "https://fakestoreapi.com/products/";

export default {
  name: 'App',
  data() {
    return {
      products: [],
    };
  },
  methods: {
    async getApi() {
      try {
        const response = await axios.get(baseUrl);
        this.products = response.data;
      } catch (error) {
        console.error(error);
      }
    },
  },
  mounted() {
    this.getApi();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->
