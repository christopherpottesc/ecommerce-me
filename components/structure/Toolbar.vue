<template>
  <v-toolbar color="blue" class="px-2 px-md-16">
    <n-link to="/" class="d-flex align-center link-toolbar">
      <img class="logo-ecommerce mr-4" src="@/assets/images/store.webp" />
      <v-toolbar-title>E-commerce ME</v-toolbar-title>
    </n-link>
  </v-toolbar>
</template>

<style lang="scss" scoped>
.v-toolbar {
  max-height: 64px !important;
}

.link-toolbar {
  color: #000;
  text-decoration: none;
}

.logo-ecommerce {
  width: 40px;
  height: 40px;
}
</style>
