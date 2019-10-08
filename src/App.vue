<template>
  <div id="app" class="container" >
    <app-filter @change-filter="updateFilter"></app-filter>
    <app-list :products="filteredProducts"></app-list>
  </div>
</template>

<script>
import Filter from './components/Filter'
import List from './components/List'
import {products} from './store.js'
export default {
  name: 'app',
  data() {
    return {
      products,      
      filterCategoryId: '',
      filterProductName: '',
      filterPriceFrom: '',
      filterPriceTo: ''
    }
  },
  computed: {
    filteredProducts() {
      let products = this.products;
      if(this.filterCategoryId) {
        products = products.filter((product) => product.categoryId === this.filterCategoryId);
      } 
      
      if(this.filterProductName) {
        products = products.filter((product) => product.name.toLowerCase().includes(this.filterProductName.toLowerCase()))
      }
      
      if(this.filterPriceFrom) {
        products = products.filter((product) => product.price >= this.filterPriceFrom)
      }

      if(this.filterPriceTo) {
        products = products.filter((product) => product.price <= this.filterPriceTo)
      }

      return products;
    }
  },
  components: {
    appFilter: Filter,
    appList: List
  },
  methods:{
    updateFilter(filter) {
      this.filterCategoryId = filter.categoryId;
      this.filterProductName = filter.searchProductName;
      this.filterPriceFrom = filter.priceFrom;
      this.filterPriceTo = filter.priceTo;
    }
  }
}
</script>

<style>
  #app {
    margin-top: 50px;
  }
</style>
