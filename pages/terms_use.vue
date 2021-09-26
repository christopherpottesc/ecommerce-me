<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="8" class="d-flex flex-column flex-md-row">
      <v-col
        cols="12"
        sm="12"
        md="12"
        class="d-flex justify-center flex-column"
      >
        <h1>Termos de Uso</h1>

        <div class="mt-16" v-for="(about, i) in abouts_texts" :key="i">
          <p class="first-line">{{ about.title }}</p>
          <span>{{ about.text }}</span>
        </div>

        <div class="d-flex flex-column align-center mx-auto mt-16">
          <p>Faça o download dos Termos de Uso em PDF:</p>
          <a
            href="https://doctour.s3-sa-east-1.amazonaws.com/files/T%C3%A9rminosyCondicionesDocTour2020.pdf"
            target="_blank"
          >
            DOWNLOAD
          </a>
        </div>
      </v-col>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      abouts_texts: [
        {
          title: "Informações gerais",
          text: `Lorem ipsum dolor sit amet. Sit temporibus possimus ut impedit quia
            sed quia alias in possimus necessitatibus eos illo repellendus id
            provident dolore ut aliquid aspernatur. A harum nostrum in minus
            sint ut neque ipsam ut rerum natus ut dolores doloribus. Ut dolor
            nemo Id explicabo sed sequi eligendi At quidem nisi vel esse
            possimus ut voluptate atque. Ad quia voluptas At aliquam excepturi
            sed veniam sint.`,
        },
        {
          title: "Item 1",
          text: `Ab molestias vitae aut quidem labore qui atque aspernatur quo autem
            quis sed velit voluptatem. Ut ipsa rerum aut ratione atque et
            consequatur officia! A Quis odit et suscipit sunt. Est totam quos ab
            aliquid unde. Sit magnam quam. Qui assumenda ipsa aut facere
            molestiae. Et animi nihil et nesciunt assumenda? Est provident
            reiciendis aut facere minima et suscipit aliquam aut recusandae
            iure.`,
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.first-line {
  letter-spacing: 0;
  color: #3b3f51;
  opacity: 1;
  font-size: 36px;
  line-height: 44px;
}
</style>