<template>
  <v-card outlined color="white">
    <v-row>
      <v-col md="4" class="pb-0">
        <div class="d-flex ml-5 mt-5">
          <v-text-field label="Search" prepend-inner-icon="mdi-magnify" outlined dense></v-text-field>
          <v-btn height="40" class="ml-2" dark depressed color="#0095E8">Cari</v-btn>
        </div>
      </v-col>
      <v-col md="8" class="containerNav">
        <div class="navAccount">
          <v-list dense width="250" max-width="250">
            <v-list-group v-for="item in items" :key="item.title" v-model="item.active" no-action>
              <template v-slot:activator>
                <div slot="prependIcon" id="customIcon">DC</div>
                <v-list-item-content>
                  <v-list-item-title v-text="item.title" class="font-weight-bold"></v-list-item-title>
                  <v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle>
                </v-list-item-content>
              </template>

              <v-list-item v-for="child in item.items" :key="child.title">
                <v-list-item-content>
                  <v-list-item-title v-text="child.title"></v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-group>
          </v-list>
        </div>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        items: [{ title: 'Setttings' }, { title: 'Logout' }],
        title: 'Dane Cooper',
        subtitle: 'Super Admin',
      },
    ],
  }),
};
</script>

<style>
.containerNav {
  position: relative;
  padding: 0;
}
.containerNav .navAccount {
  position: absolute;
  top: 1rem;
  right: 6rem;
}

#customIcon {
  background-color: #eaecf3;
  border-radius: 50%;
  font-size: 1.5rem;
  font-weight: bold;
  padding: 5px 7px;
  margin-right: 10px;
}
</style>
