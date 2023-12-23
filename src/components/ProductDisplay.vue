<template>
  <div class="all">
    <div class="app-container">
      <img
        :src="product.image"
        alt="Product Image"
        style="
          max-width: 200px;
          max-height: 300px;
          float: left;
          margin-left: 100px;
          margin-top: 0px;
        "
      />
      <div style="margin-left: 100px; margin-top: 30px; margin-bottom: 1px">
        <p
          style="
            font-family: Arial, Helvetica, sans-serif;
            font-size: x-large;
            color: #720060;
          "
        >
          {{ product.title }}
        </p>
        <p>
          <span style="float: left">{{ product.category }}</span>
          <span style="float: right">{{ product.rating.rate }}/5</span>
        </p>
        <br />
        <hr />
        <p
          style="
            font-family: 'Times New Roman', Times, serif;
            font-size: larger;
          "
        >
          {{ product.description }}
        </p>
        <hr />
        <p
          style="
            font-family: Arial, Helvetica, sans-serif;
            font-size: x-large;
            color: #720060;
          "
        >
          ${{ product.price }}
        </p>

        <button
          class="border-button2"
          style="text-align: center; margin-top: 10px; margin-left: 0px"
        >
          Buy Now
        </button>
        <button
          class="border-button"
          @click="getNextProduct"
          style="text-align: center; margin-top: 10px; margin-left: 40px"
        >
          Next Product
        </button>

        <div v-if="loading" class="loader-overlay">
          <div class="loader"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: Object,
  },
  data() {
    return {
      loading: false,
    };
  },

  methods: {
    getNextProduct() {
      // Show loader before loading data
      this.loading = true;

      // Simulate API call (replace with your actual API call)
      setTimeout(() => {
        // Emit an event to ask the parent component to load the next product
        this.$emit("next-product");

        // Hide loader after data is loaded
        this.loading = false;
      }, 1000); // Simulated API call time (2 seconds)
    },
  },
};
</script>

<style scoped>
.all {
  background-color: #fde2ff;
  height: 70vh;
}
.app-container {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 10px;
  width: 900px;
  height: 600px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
}

.border-button {
  background-color: transparent; /* Latar belakang transparan */
  color: #720060; /* Warna teks sesuai kebutuhan Anda */
  border: 2px solid #720060; /* Garis sesuai kebutuhan Anda */
  padding: 10px 15px; /* Sesuaikan dengan padding yang diinginkan */
  border-radius: 5px;
  cursor: pointer;
  width: 230px;
}

.border-button2 {
  background-color: #720060; /* Latar belakang transparan */
  color: #fff; /* Warna teks sesuai kebutuhan Anda */
  border: 2px solid #720060; /* Garis sesuai kebutuhan Anda */
  border-radius: 5px;
  cursor: pointer;
  width: 230px;
}

.loader-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.loader {
  border: 16px solid #f3f3f3;
  border-top: 16px solid #3498db;
  border-radius: 50%;
  width: 120px;
  height: 120px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>

<!-- 
    <template>
      <div class="app-container">
        <img :src="product.image" alt="Product Image" style="max-width: 200px; max-height: 300px; float: left; margin-right: 70px; margin-top: 50px;" />
        <div class="content-container">
          <p>{{ product.title }}</p>
          <p>{{ product.category }} &nbsp;&nbsp;&nbsp;&nbsp; &nbsp; {{ product.rating.rate }}/5</p>
          
          <hr class="line">
          <p>{{ product.description }}</p>
          <hr class="line">
          <p>${{ product.price }}</p>
    
          <div class="button-container">
            <button @click="getNextProduct">Next Product</button>
          </div>
        </div>
      </div>
    </template>
    
    <script>
    export default {
      props: {
        product: Object,
      },
      methods: {
        getNextProduct() {
          this.$emit("next-product");
        },
      },
    };
    </script>
    
    <style scoped>
    .app-container {
      background-color: #FFFFFF;
      padding: 20px;
      border-radius: 10px;
      text-align: center;
      width: 900px;
      height: 500px;
      margin: 0 auto;
      margin-bottom: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    
    .content-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin-top: 40px;
      margin-bottom: 1px;
      ;
    }
    
    .button-container {
      text-align: right;
      margin-top: 10px;
    }
    
    .line {
      width: 100%;
      border: none;
      height: 1px;
      color: #000; /* Warna garis, sesuaikan dengan kebutuhan Anda */
      background-color: #000; /* Warna garis, sesuaikan dengan kebutuhan Anda */
      margin: 10px 0;
    }
    </style>
     -->
