<template>
  <v-row justify="center" align="center" style="height: calc(100vh - 36px - 64px)">
    <v-col cols="12" sm="12" md="10" class="d-flex flex-column flex-md-row">
      <FavoritesList :favorites="favorites"></FavoritesList>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data(){
    return{
      favorites: []
    }
  },
  created(){
    this.fetchProducts()
  },
  methods: {
    async fetchProducts(){
      this.favorites = await this.$axios.$get('https://fakestoreapi.com/products')
      console.log(this.favorites)
    }
  }
}
</script>