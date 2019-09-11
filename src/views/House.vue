<template>
  <div class="house">
    House Details
    <h1>Built in: {{house.year}}</h1>
    <h5>{{house.bedrooms}} bedroom, {{house.bathrooms}} bathroom</h5>
    <h5></h5>
    <img :src="house.imgUrl" />
    <h5>${{house.price}}</h5>
    <p>{{house.description}}</p>
    <button class="btn btn-danger" @click="deleteThisHouse">Delete</button>
  </div>
</template>


<script>
export default {
  name: "house",
  data() {
    return {};
  },
  mounted() {
    let payload = {
      houseId: this.$route.params.houseId
    };
    this.$store.dispatch("getHouseById", payload);
  },
  computed: {
    house() {
      return this.$store.state.activeHouse;
    }
  },
  methods: {
    deleteThisHouse() {
      this.$store.dispatch("deleteHouse", this.house._id);
    }
  },
  components: {}
};
</script>


<style scoped>
img {
  height: 500px;
}
</style>