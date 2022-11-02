<template>
  <v-card max-width="250" height="100vh">
    <v-card-title>
      <v-img :src="logoPath" contain max-height="40" max-width="90"></v-img>
    </v-card-title>
    <v-card-subtitle>
      <i>Version 0.12</i> <span style="color: #98654f">Beta</span>
    </v-card-subtitle>
    <v-list dense>
      <v-list-group
        v-for="item in items"
        :key="item.title"
        v-model="item.active"
        no-action
      >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item-content>
        </template>

        <v-list-item
          v-for="child in item.items"
          :key="child.title"
          class="pl-4"
        >
          <v-list-item-icon class="mr-2">
            <v-icon v-text="child.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="child.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        items: [
          { title: "Harga", icon: "mdi-land-plots" },
          { title: "Kategori", icon: "mdi-land-plots" },
          { title: "Product Listing", icon: "mdi-land-plots" },
        ],
        title: "Product",
      },
      {
        items: [
          { title: "Banner", icon: "mdi-land-plots" },
          { title: "Promo Produk", icon: "mdi-land-plots" },
          { title: "Voucher", icon: "mdi-land-plots" },
        ],
        title: "Marketing",
      },
      {
        items: [
          { title: "Zona", icon: "mdi-land-plots" },
          { title: "Geofencing", icon: "mdi-land-plots" },
          { title: "Akun Toko", icon: "mdi-land-plots" },
          { title: "Membership Toko", icon: "mdi-land-plots" },
          { title: "Stock", icon: "mdi-land-plots" },
          { title: "Human Resource", icon: "mdi-land-plots" },
        ],
        title: "Toko",
      },
      {
        items: [
          { title: "Akun Driver", icon: "mdi-land-plots" },
          { title: "Aktifitas Order", icon: "mdi-land-plots" },
        ],
        title: "Driver",
      },
      {
        items: [
          { title: "Akun Pengguna", icon: "mdi-land-plots" },
          { title: "Membership Pengguna", icon: "mdi-land-plots" },
        ],
        title: "Pengguna",
      },
      {
        items: [
          { title: "Komplain", icon: "mdi-land-plots" },
          { title: "Aktifitas Order", icon: "mdi-land-plots" },
        ],
        title: "Customer Service",
      },
    ],
    logoPath: require("@/assets/logo_ahamart.png"),
  }),
};
</script>

<style></style>
