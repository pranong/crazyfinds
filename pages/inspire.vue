<template>
  <v-row>
    <v-col
      v-for="index in 12"
      lg="3"
      :key="index"
      sm="12"
      md="6"
      class="text-center"
    >
      <v-card :loading="loading" cols="12">
        <v-container>
          <img src="/v.png" alt="Vuetify.js" class="pt-5 ma-3" />
          <blockquote>
            1990 Blink-182 Single stitch
            <footer>
              <small>
                <em>$900</em>
              </small>
            </footer>
          </blockquote>
        </v-container>
      </v-card>
    </v-col>
    <v-col cols="auto">
      <v-dialog transition="dialog-bottom-transition" max-width="600">
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            fab
            fixed
            right
            bottom
            x-large
            v-bind="attrs"
            v-on="on"
            :style="{ bottom: '5%' }"
          >
            <v-icon>mdi-filter</v-icon>
          </v-btn>
        </template>
        <template v-slot:default="dialog">
          <v-card>
            <v-card-text>
              <div class="text-h3 pa-12">Filter!</div>
            </v-card-text>
            <v-card-actions class="justify-end">
              <v-btn text @click="dialog.value = false">DONE</v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "InspirePage",
  data() {
    return {
      drawer: false,
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
    };
  },
  methods: {
    async alerting() {
      await this.$swal.fire("Any fool can use a computer");
    },
  },
};
</script>
