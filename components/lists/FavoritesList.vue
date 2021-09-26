<template>
  <v-row no-gutters>
    <v-col cols="12" sm="12" md="4" v-for="(prod, i) in favorites" :key="i">
      <div class="card-item d-flex flex-column pa-4">
        <div class="card-item__header d-flex justify-space-between">
          <span>$ {{ prod.price }}</span>
        </div>
        <div class="d-flex flex-column">
          <img
            class="card-item__image"
            :src="prod.image"
            style="width: 50px; height: 50px"
          />
          <div class="card-item__data">
            <p>{{ prod.category }}</p>
            <p>{{ prod.title }}</p>
          </div>
          <v-btn depressed elevation="2">ADICIONAR</v-btn>
        </div>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: {
    favorites: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
    };
  },
  methods: {
  },
};
</script>

<style lang="scss" scoped>
.card-item {
  border: 1px solid red;
  color: #3b3f51;
  letter-spacing: 0px;
  opacity: 1;

  &header {
    font-size: 16px;
  }

  &image {
    width: 95px;
    height: 125px;
  }

  &data {
    font-size: 12px;
  }
}
</style>