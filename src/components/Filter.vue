<template>
  <div class="header-search mb-4">
    <div class="input-group mr-3">
      <input type="text" class="form-control" placeholder="Search" v-model="filter.searchProductName">
    </div>
    <div class="input-group mr-3">
      <select class="form-control" v-model="filter.categoryId">
        <option value="">Select category</option>
        <option 
          v-for="category in categories"
          :key="category.id"
          :value="category.id">
          {{ category.title }}
          </option>
      </select>
    </div>

    <div class="input-group mr-3">      
      <input type="number" placeholder="From" class="form-control" v-model.trim.number="filter.priceFrom">
      <span class="input-group-text"> - </span>
      <input type="number" placeholder="To" class="form-control" v-model.trim.number="filter.priceTo">
    </div>

    <button class="btn btn-primary"
      @click="applyFilter"
    >Apply</button>
  </div>
</template>

<script>
import {categories} from '../store'
export default {
  data() {
    return {
      categories,
      filter: {
        categoryId: '',
        searchProductName: '',
        priceFrom: '',
        priceTo: ''
      }
    }
  },
  methods: {
    applyFilter() {
      this.$emit('change-filter', this.filter)
    }
  }
}
</script>

<style lang="scss" scoped>
  .header-search {
    display: flex;
  }
</style>