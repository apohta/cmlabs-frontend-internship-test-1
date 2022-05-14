<template>
  <div>
    <Navbar />
    <div v-for="(product, i) in filter_category.meals" :key="i">
      <div class="ml-5">
        <b-card :title="product.strMeal" :sub-title="product.strCategory" :img-src="product.strMealThumb" img-left
          img-width="30%" img-height="30%">
          <b-card-text class="text-justify">
            <h5>Instruction</h5>
            {{ product.strInstructions }}
          </b-card-text>

          <b-card-text>
            <h5>Ingredients</h5>
            <b-list-group>
              <b-list-group-item class="d-flex justify-content-between align-items-center">
                {{ product.strIngredient1 }}
                <b-badge variant="primary" pill>{{
                    product.strMeasure1
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item class="d-flex justify-content-between align-items-center">
                {{ product.strIngredient2 }}
                <b-badge variant="primary" pill>{{
                    product.strMeasure2
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item class="d-flex justify-content-between align-items-center">
                {{ product.strIngredient3 }}
                <b-badge variant="primary" pill>{{
                    product.strMeasure3
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item class="d-flex justify-content-between align-items-center">
                {{ product.strIngredient4 }}
                <b-badge variant="primary" pill>{{
                    product.strMeasure4
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item class="d-flex justify-content-between align-items-center">
                {{ product.strIngredient5 }}
                <b-badge variant="primary" pill>{{
                    product.strMeasure5
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item class="d-flex justify-content-between align-items-center">
                {{ product.strIngredient6 }}
                <b-badge variant="primary" pill>{{
                    product.strMeasure6
                }}</b-badge>
              </b-list-group-item>
            </b-list-group>
          </b-card-text>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  async asyncData({ store, params }) {
    await Promise.all([
      store.dispatch("category/getFilterCategoryData", params.id),
    ]);
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
      filter_category: (state) => state.filter_category,
    }),
  },
  methods: {
    ...mapActions("category", ["getFilterCategoryData"]),
  },
};
</script>
