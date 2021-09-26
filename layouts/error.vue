<template>
  <v-row justify="center" align="center" style="height: calc(100vh - 36px - 64px)">
    <v-col cols="12" sm="12" md="8" class="d-flex flex-column flex-md-row">
      <v-col cols="12" sm="12" md="6" class="d-flex justify-center flex-column">
        <p class="first-line">OPS...</p>
        <p class="second-line">{{ errorMessage }}</p>
        <p class="second-line">
          Clique <a class="button-back" href="/">aqui</a> para voltar para o
          início.
        </p>
      </v-col>
      <v-col cols="12" sm="12" md="6" class="d-flex justify-center justify-md-end">
        <img
          class="image404"
          alt="Image Not Found - 404"
          src="@/assets/images/image_404.png"
        />
      </v-col>
    </v-col>
  </v-row>
</template>

<script>
export default {
  layout: "empty",
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      pageNotFound: "404 Not Found",
      otherError: "An error occurred",
    };
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError;
    return title;
  },
  computed: {
    errorMessage() {
      if (this.error.statusCode === 404) {
        return "Está página não foi encontrada.";
      }
      return "Ocorreu um erro!";
    },
  },
};
</script>

<style scoped lang="scss">
.first-line {
  letter-spacing: 0;
  color: #3b3f51;
  opacity: 1;
  font-size: 36px;
  line-height: 44px;
}

.second-line {
  letter-spacing: 0;
  color: #3b3f51;
  opacity: 1;
  font-size: 20px;
  line-height: 28px;
}

.button-back {
  text-decoration: underline;
  cursor: pointer;
}

.image {
  height: 500px;
  width: 500px;
}
</style>
