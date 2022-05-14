<template>
  <div>
    <Navbar />
    <h1 v-for="(product, i) in params" :key="i">{{ product.name }}</h1>
    <b-container class="bv-example-row">
      <b-row>
        <b-col v-for="(product, i) in filter.meals" :key="i"
          ><b-button
            :to="{
              name: 'Category-list_id',
              params: { id: product.idMeal },
            }"
            style="max-width: 15rem"
            variant="light"
          >
            <img :src="product.strMealThumb" style="width: 13rem" />
            <h5 class="text-center text-dark">
              {{ product.strMeal }}
            </h5>
          </b-button></b-col
        >
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  async asyncData({ store, params }) {
    await Promise.all([store.dispatch("category/getFilterData", params.name)]);
    return;
  },
  data() {
    return {
      product: [],
    };
  },
  computed: {
    ...mapState("category", {
      filter: (state) => state.filter,
    }),
  },
  methods: {
    ...mapActions("category", ["getFilterData"]),
  },
};
</script>
