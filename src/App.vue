<template>
  <div id="app" class="container" >
    <app-filter @change-filter="filterCategoryId = $event"></app-filter>
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
      filterCategoryId: ''
    }
  },
  computed: {
    filteredProducts() {
      if(!this.filterCategoryId) {
        return this.products
      } 
      return this.products.filter((product) => {
        return product.categoryId === this.filterCategoryId
      })
    }
  },
  components: {
    appFilter: Filter,
    appList: List
  }
}
</script>

<style>
#app {
  
}
</style>
