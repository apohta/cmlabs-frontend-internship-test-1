<template>
  <div>
    <Navbar />
    <h1 v-for="(items, i) in params" :key="i">{{ items.name }}</h1>
    <b-container class="bv-example-row">
      <b-row>
        <b-col v-for="(items, i) in filter.meals" :key="i"
          ><b-button
            :to="{
              name: 'category-id',
              params: { id: items.idMeal },
            }"
            style="max-width: 15rem"
            variant="light"
          >
            <img :src="items.strMealThumb" style="width: 13rem" />
            <h5 class="text-center text-dark">
              {{ items.strMeal }}
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
      items: [],
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
