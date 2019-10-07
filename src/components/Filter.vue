<template>
  <div>
    <div class="input-group mb-3">
      <input type="text" class="form-control" placeholder="Search"  >
    </div>
    <div class="input-group mb-3">
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

    <div class="input-group mb-3">      
      <input type="number" placeholder="From" class="form-control">
      <span class="input-group-text"> - </span>
      <input type="number" placeholder="To" class="form-control">
    </div>

    <button class="btn btn-primary mb-5"
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
      selectedCategoryId: ''
    }
  },
  methods: {
    applyFilter() {
      this.$emit('change-filter', this.selectedCategoryId)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>