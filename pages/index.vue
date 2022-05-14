<template>
  <div>
    <Navbar />
    <div class="section-1 text-center mb-5">
      <p class="h1">Category</p>
    </div>
    <div class="section-content">
      <b-container class="bv-example-row">
        <b-row class="mb-3">
          <b-col v-for="(product, i) in category.slice(0, 4)" :key="i">
            <b-button
              :to="{
                name: 'Category-list_name',
                params: { name: product.strCategory },
              }"
              style="max-width: 20rem"
              variant="light"
            >
              <img :src="product.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ product.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
        <b-row class="mb-3">
          <b-col v-for="(product, i) in category.slice(5, 9)" :key="i">
            <b-button
              :to="{
                name: 'Category-list_name',
                params: { name: product.strCategory },
              }"
              style="max-width: 20rem"
              variant="light"
            >
              <img :src="product.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ product.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
        <b-row class="mb-3">
          <b-col v-for="(product, i) in category.slice(10, 14)" :key="i">
            <b-button
              :to="{
                name: 'Category-list_name',
                params: { name: product.strCategory },
              }"
              style="max-width: 20rem"
              variant="light"
            >
              <img :src="product.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ product.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
        <b-row class="mb-3">
          <b-col v-for="(product, i) in category.slice(15, 19)" :key="i">
            <b-button
              :to="{
                name: 'Category-list_name',
                params: { name: product.strCategory },
              }"
              style="max-width: 20rem"
              variant="light"
            >
              <img :src="product.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ product.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  async asyncData({ store }) {
    await Promise.all([store.dispatch("category/getCategoryData")]);
    return;
  },
  data() {
    return {
      fields: ["idCategory"],
      product: [],
    };
  },
  computed: {
    ...mapState("category", {
      category: (state) => state.category,
    }),
  },
  methods: {
    ...mapActions("category", ["getCategoryData"]),
  },
};
</script>
