<template>
  <div>
    <Navbar />
    <div v-for="(items, i) in filter_category.meals" :key="i">
      <div class="ml-5">
        <b-card
          :title="items.strMeal"
          :sub-title="items.strCategory"
          :img-src="items.strMealThumb"
          img-left
          img-width="30%"
          img-height="30%"
        >
          <b-card-text class="text-justify">
            <h5>Instruction</h5>
            {{ items.strInstructions }}
          </b-card-text>

          <b-card-text>
            <h5>Ingredients</h5>
            <b-list-group>
              <b-list-group-item
                class="d-flex justify-content-between align-items-center"
              >
                {{ items.strIngredient1 }}
                <b-badge variant="primary" pill>{{
                  items.strMeasure1
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item
                class="d-flex justify-content-between align-items-center"
              >
                {{ items.strIngredient2 }}
                <b-badge variant="primary" pill>{{
                  items.strMeasure2
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item
                class="d-flex justify-content-between align-items-center"
              >
                {{ items.strIngredient3 }}
                <b-badge variant="primary" pill>{{
                  items.strMeasure3
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item
                class="d-flex justify-content-between align-items-center"
              >
                {{ items.strIngredient4 }}
                <b-badge variant="primary" pill>{{
                  items.strMeasure4
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item
                class="d-flex justify-content-between align-items-center"
              >
                {{ items.strIngredient5 }}
                <b-badge variant="primary" pill>{{
                  items.strMeasure5
                }}</b-badge>
              </b-list-group-item>
              <b-list-group-item
                class="d-flex justify-content-between align-items-center"
              >
                {{ items.strIngredient6 }}
                <b-badge variant="primary" pill>{{
                  items.strMeasure6
                }}</b-badge>
              </b-list-group-item>
            </b-list-group></b-card-text
          >
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
      items: [],
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
