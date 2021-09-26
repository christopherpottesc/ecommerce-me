<template>
  <v-row no-gutters justify="space-between">
    <div class="d-flex cotent-data">
      <div>
        <div class="user-name">Hi, {{ user.name }}</div>
        <div class="user-addres">{{ user.address }}</div>
      </div>
      <v-menu offset-y>
        <template #activator="{ on: onMenu }">
          <v-tooltip bottom>
            <template #activator="{ on: onTooltip }">
              <v-btn icon v-on="{ ...onMenu, ...onTooltip }">
                <v-icon dark> mdi-chevron-down </v-icon>
              </v-btn>
            </template>
            <span>Alterar endereço</span>
          </v-tooltip>
        </template>
        <v-list>
          <v-list-item v-for="(address, i) in adresses" :key="i">
            <v-list-item-title @click="changeAddress(address)">
              {{ address }}
            </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </div>
    <div>
      <div class="content-icons">
        <v-tooltip bottom>
          <template v-slot:activator="{ on, attrs }">
            <n-link to="/cart" class="mr-4">
              <v-icon color="primary" v-bind="attrs" v-on="on">
                mdi-cart
              </v-icon>
            </n-link>
          </template>
          <span>Ver meu carrinho</span>
        </v-tooltip>
        <v-tooltip bottom>
          <template v-slot:activator="{ on, attrs }">
            <n-link to="/profile" class="mr-4">
              <v-icon color="primary" v-bind="attrs" v-on="on">
                mdi-baby-face-outline
              </v-icon>
            </n-link>
          </template>
          <span>Ver meu perfil</span>
        </v-tooltip>
      </div>
    </div>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      adresses: ["1725 Sloug Avenue", "Av. João Gomes Nogueira, 703"],
      user: {
        name: "Dwight",
        address: "1725 Sloug Avenue",
      },
    };
  },
  methods: {
    changeAddress(address) {
      return (this.user.address = address);
    },
  },
};
</script>
<style lang="scss" scoped>
.content-data {
  display: flex;
  flex-direction: column;
}

.content-profile {
  display: flex;
  text-align: left;
}

.content-dropdown {
  align-items: center;
  display: flex;
  margin-left: 12px;
}

.user-name {
  font-size: 20px;
  line-height: 24px;
  color: #3b3f51;
}

.user-address {
  font-size: 12px;
  line-height: 16px;
  color: #3b3f51;
}
</style>