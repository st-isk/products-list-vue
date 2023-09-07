<template>
  <div class="app">
    <div class="top__bar">
      <h1>List of products</h1>
      <CustomButton @click="showDialog">Add a product</CustomButton>
    </div>
    <CustomDialogWindow v-model:show="dialogVisible">
      <AddProductMenu
        @create="createProduct"
      />
    </CustomDialogWindow>
    <ProductsList 
      :products=products
      @remove="removeProduct"
    />
  </div>
</template>

<script>
import ProductsList from './components/ProductsList.vue';
import CustomDialogWindow from './UI/CustomDialogWindow.vue';
import AddProductMenu from './components/AddProductMenu.vue';
import CustomButton from './UI/CustomButton.vue';

export default {
  name: 'App',
  components: { ProductsList, CustomDialogWindow, AddProductMenu, CustomButton },
  data() {
    return {
      products: [],
      dialogVisible: false,
    }
  },
  methods: {
    removeProduct(product){
        if(product.isDeleted){
          product.isDeleted = false;
          let curProductIndx = this.products.indexOf(product);
          this.products.unshift(this.products[curProductIndx]);
          this.products = this.products.filter((product, indx) => indx !== curProductIndx + 1);
          localStorage.setItem("products", JSON.stringify(this.products));
        }
        else{
          product.isDeleted = true;
          let curProductIndx = this.products.indexOf(product);
          this.products.push(this.products[curProductIndx]);
          this.products = this.products.filter((product, indx) => indx !== curProductIndx);
          localStorage.setItem("products", JSON.stringify(this.products));
        }
    },
    createProduct(product) {
        this.products.unshift(product);
        localStorage.setItem("products", JSON.stringify(this.products));
        this.dialogVisible = false;
    },
    showDialog(){
        this.dialogVisible = true;
    },
  },
  mounted() {
    if(localStorage.getItem("products") !== null){
      this.products = JSON.parse(localStorage.getItem("products"));
    }
  },
}
</script>

<style>
  *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
  }

  .app {
      padding: 10px 25px;
  }

  .top__bar {
      display: flex;
      justify-content: space-between;
  }
</style>
