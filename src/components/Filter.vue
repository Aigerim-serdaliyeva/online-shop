<template>
  <div class="header-search mb-4">
    <div class="input-group mr-3">
      <input type="text" class="form-control" placeholder="Search"  v-model="searchCategoryName">
    </div>
    <div class="input-group mr-3">
      <select class="form-control" v-model="selectedCategoryId">
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
      <input type="number" placeholder="From" class="form-control">
      <span class="input-group-text"> - </span>
      <input type="number" placeholder="To" class="form-control">
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
      selectedCategoryId: '',
      searchCategoryName: ''
    }
  },
  methods: {
    applyFilter() {
      this.$emit('change-filter', this.selectedCategoryId)

      this.$emit('searchFilter', this.searchCategoryName)
    }
  }
}
</script>

<style lang="scss" scoped>
  .header-search {
    display: flex;
  }
</style>