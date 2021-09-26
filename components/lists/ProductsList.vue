<template>
  <v-row no-gutters class="d-flex flex-column">
    <v-row no-gutters class="my-8" justify="space-between" style="width: 100%">
      <v-col cols="12" sm="12" md="12" class="d-flex flex-column flex-md-row">
        <v-text-field
          v-model="search"
          solo
          hide-details
          label="Procure por nome ou categoria"
          append-icon="mdi-magnify"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row no-gutters align="center" class="mt-4 mb-8">
      <v-col cols="6" sm="12" md="8">
        <span class="title-products">Produtos</span>
      </v-col>

      <v-col cols="6" sm="12" md="4">
        <v-select
          :items="categories"
          @change="listPerCategory(category)"
          v-model="category"
          label="Categorias"
          hide-details
          solo
        >
        </v-select>
      </v-col>
    </v-row>

    <v-row no-gutters>
      <v-col
        cols="6"
        sm="12"
        md="4"
        v-for="(prod, i) in fitleredProducts"
        :key="i"
        class="pa-2"
      >
        <div
          class="card-item d-flex flex-column justify-space-between pa-4"
          style="min-height: 300px"
        >
          <div class="card-item__header d-flex justify-space-between">
            <span>$ {{ prod.price }}</span>
            <v-icon v-if="notFavorited" @click="favoritar(prod)">
              mdi-heart-outline
            </v-icon>
            <v-icon v-else @click="favoritar(item)"> mdi-cards-heart </v-icon>
          </div>
          <div class="d-flex justify-center">
            <img
              class="card-item__image"
              :src="prod.image"
              style="width: 95px; height: 125px"
            />
          </div>
          <div class="card-item__data">
            <p class="mb-0">{{ prod.category }}</p>
            <v-tooltip bottom>
              <template v-slot:activator="{ on, attrs }">
                <p v-bind="attrs" v-on="on" class="text-title mb-0">
                  {{ prod.title }}
                </p>
              </template>
              <span>{{ prod.title }}</span>
            </v-tooltip>
          </div>
          <v-btn depressed elevation="2" @click="addToCart(prod)">
            ADICIONAR
          </v-btn>
        </div>
      </v-col>
    </v-row>
    <v-snackbar v-model="snackbar.show" top>
      <span>{{ snackbar.text }}</span>
      <span>
        Ver lista de favotiros clique
        <n-link target="_blank" to="/favorites" class="mr-4"> aqui </n-link>
      </span>
      <template v-slot:action="{ attrs }">
        <v-btn color="green" text v-bind="attrs" @click="snackbar.show = false">
          Fechar
        </v-btn>
      </template>
    </v-snackbar>
  </v-row>
</template>

<script>
export default {
  props: {
    products: {
      type: Array,
      default: () => [],
    },
    categories: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      notFavorited: true,
      snackbar: {
        show: false,
        text: "",
      },
      search: "",
      category: "",
      fitleredProducts: [],
    };
  },
  mounted() {
    this.fitleredProducts = this.products;
  },
  watch: {
    search() {
      if (this.search.length < 2) {
        this.fitleredProducts = this.products;
      } else {
        const filtered = this.products.filter((u) => {
          return (
            u.title.toLowerCase().includes(this.search.toLowerCase()) ||
            u.category.toLowerCase().includes(this.search.toLowerCase())
          );
        });
        this.fitleredProducts = filtered;
      }
    },
  },
  methods: {
    addToCart(prod) {
      console.log("Produto: " + prod + " adicionado no carrinho");
    },
    favoritar(prod) {
      this.notFavorited = !this.notFavorited;
      this.snackbar.show = true;
      this.snackbar.text =
        "O item: " + prod.title + " foi adicionar a sua lista de favoritos.";
    },
    listPerCategory(category) {
      const filtered = this.products.filter((u) => {
        return u.category.toLowerCase().includes(category.toLowerCase());
      });
      this.fitleredProducts = filtered;
    },
  },
};
</script>

<style lang="scss" scoped>
.title-products {
  font-size: 20px;
  line-height: 24px;
  letter-spacing: 0px;
  color: #3b3f51;
  opacity: 1;
}

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

.text-title {
  white-space: nowrap;
  width: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>