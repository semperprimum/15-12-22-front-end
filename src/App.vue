<template>
  <div class="container">
    <Header @toggle-add-product="toggleAddProduct" title="Учет Товаров" />
    <div v-show='showAddProducts'>
    <AddProduct @add-product="addProduct" />
    </div>
    <Products @delete-product="deleteProduct" :products="products"/>
  </div>
</template>

<script>
import Header from "./components/Header";
import Products from "./components/Products";
import AddProduct from "./components/AddProduct";


export default {
  name: "App",
  components: {
    Header,
    Products,
    AddProduct,
  },
  data() {
    return {
      products: [],
      showAddProducts: false
    }
  },
  methods: {
    toggleAddProduct () {
      this.showAddProducts = !this.showAddProducts
    },

    addProduct(product) {
        this.products = [...this.products, product]
    },

    deleteProduct(id) {
      if(confirm('Вы уверены?')) {
        this.products = this.products.filter((product) => product.id !== id)
      }
    },
  },
  created() {
    this.products = [
      {
        id: 1,
        text: 'Шоколад',
        qt: '120',
        date: '2022-12-01',
        price: 100,
        totalPrice: 12000,
      },
      {
        id: 2,
        text: 'Лимонад 2л.',
        qt: '50',
        date: '2022-11-28',
        price: 400,
        totalPrice: 20000,
      },
      {
        id: 3,
         text: 'Конфеты',
        qt: '200',
        date: '2022-12-10',
        price: 50,
        totalPrice: 10000,
      }
    ]
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Poppins", sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
