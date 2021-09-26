<template>
  <v-row justify="center" align="start" style="height: calc(100vh - 36px - 64px)">
    <v-col cols="12" sm="12" md="10" class="d-flex flex-column">
      <HeaderHome />
      <ProductsList :products="products" :categories="categories"></ProductsList>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data(){
    return{
      products: [],
      categories: []
    }
  },
  mounted(){
    this.fetchProducts()
    this.fetchCategories()
  },
  methods: {
    async fetchProducts(){
      this.products = await this.$axios.$get('https://fakestoreapi.com/products')
      console.log(this.products)
    },
    async fetchCategories(){
      this.categories = await this.$axios.$get('https://fakestoreapi.com/products/categories')
      console.log(this.categories)
    },
  }
}
</script>