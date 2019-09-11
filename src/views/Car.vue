<template>
  <div class="car">
    Car Deets
    <h1>Make: {{car.make}}</h1>
    <h5>Model: {{car.model}}</h5>
    <h5>Year: {{car.year}}</h5>
    <h5>Price: ${{car.price}}</h5>
    <img :src="car.imgUrl" alt />
    <h5>{{car.description}}</h5>
    <button class="btn btn-danger" @click="deleteThisCar">Delete</button>
  </div>
</template>


<script>
export default {
  name: "car",
  data() {
    return {};
  },
  mounted() {
    let payload = {
      carId: this.$route.params.carId
    };
    this.$store.dispatch("getCarById", payload);
  },
  computed: {
    car() {
      return this.$store.state.activeCar;
    }
  },
  methods: {
    deleteThisCar() {
      this.$store.dispatch("deleteCar", this.car._id);
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