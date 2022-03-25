<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" fixed app>
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!-- Nav Bar -->
    <v-app-bar :clipped-left="clipped" fixed dense app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />

      <v-toolbar-title v-text="title" />

      <v-spacer />

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
        <!-- <v-icon>mdi-heart-outline</v-icon> -->
      </v-btn>
      <v-badge
        bordered
        color="error"
        :content="cart.length"
        bottom
        overlap
        offset-x="20"
        offset-y="25"
      >
        <v-btn icon>
          <v-icon>mdi-cart</v-icon>
        </v-btn>
      </v-badge>
      <!-- Login details -->
    </v-app-bar>
    <!-- Body -->
    <v-main>
      <v-container class="pt-10">
        <Nuxt />
      </v-container>
    </v-main>
    <!-- Footer -->
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
    <!-- others -->
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      cart: [
        { stkId: "1", itemName: "A", price: "999" },
        { stkId: "2", itemName: "A", price: "999" },
        { stkId: "3", itemName: "A", price: "999" },
        { stkId: "4", itemName: "A", price: "999" },
      ],
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-home",
          title: "Home",
          to: "/",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Inspire",
          to: "/inspire",
        },
      ],
      miniVariant: true,
      right: true,
      rightDrawer: false,
      title: "Crazyfinds",
    };
  },
};
</script>
