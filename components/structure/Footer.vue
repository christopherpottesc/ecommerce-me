<template>
  <v-footer :absolute="fixed" app class="px-2 px-md-16">
    <div>
      &copy; {{ new Date().getFullYear() }} - Desenvolvido por Christopher
      Pottes
    </div>
    <v-spacer />
    <div class="d-flex">
      <n-link to="/terms_use" class="mr-4">
        Termos de Uso
      </n-link>
      <n-link to="/privacy" class="ml-4">
        Políticas de Privacidade
      </n-link>
    </div>
  </v-footer>
</template>
<script>
export default {
  data() {
    return {
      fixed: false,
    };
  },
};
</script>