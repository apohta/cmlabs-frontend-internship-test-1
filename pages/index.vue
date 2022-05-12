<template>
  <div>
    <Navbar />
    <!-- <div class="nav-bar">
      <b-navbar class="ml-5 mr-5 mb-3" type="light" variant="light">
        <b-navbar-brand href="#">Let's Eat</b-navbar-brand>
        <b-navbar-nav class="ml-auto">
          <b-nav-item right>Home</b-nav-item>
          <b-nav-item right>Food</b-nav-item>
          <b-nav-item right>Category</b-nav-item>
        </b-navbar-nav>
      </b-navbar>
    </div> -->
    <div class="section-1 text-center mb-5">
      <div class="mb-2">
        <b-icon
          icon="emoji-heart-eyes"
          style="color: #7952b3"
          font-scale="4"
          class="m-2"
        ></b-icon>
        <b-icon
          icon="emoji-heart-eyes"
          style="color: #7952b3"
          font-scale="4"
          class="m-2"
        ></b-icon>
        <b-icon
          icon="emoji-heart-eyes"
          style="color: #7952b3"
          font-scale="4"
          class="m-2"
        ></b-icon>
      </div>
      <p class="h1">Find Your Favorite Food!</p>
    </div>
    <div class="section-content">
      <b-container class="bv-example-row">
        <b-row class="mb-3">
          <b-col v-for="(items, i) in category.slice(0, 4)" :key="i">
            <b-button
              :to="{
                name: 'category-name',
                params: { name: items.strCategory },
              }"
              style="max-width: 15rem"
              variant="light"
            >
              <img :src="items.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ items.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
        <b-row class="mb-3">
          <b-col v-for="(items, i) in category.slice(5, 9)" :key="i">
            <b-button
              :to="{
                name: 'category-name',
                params: { name: items.strCategory },
              }"
              style="max-width: 15rem"
              variant="light"
            >
              <img :src="items.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ items.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
        <b-row class="mb-3">
          <b-col v-for="(items, i) in category.slice(10, 14)" :key="i">
            <b-button
              :to="{
                name: 'category-name',
                params: { name: items.strCategory },
              }"
              style="max-width: 15rem"
              variant="light"
            >
              <img :src="items.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ items.strCategory }}
              </h2>
            </b-button>
          </b-col>
        </b-row>
        <b-row class="mb-3">
          <b-col v-for="(items, i) in category.slice(15, 19)" :key="i">
            <b-button
              :to="{
                name: 'category-name',
                params: { name: items.strCategory },
              }"
              style="max-width: 15rem"
              variant="light"
            >
              <img :src="items.strCategoryThumb" style="width: 13rem" />
              <h2 class="text-center text-dark">
                {{ items.strCategory }}
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
      items: [],
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
