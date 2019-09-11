<template>
  <div class="house col-3 border rounded" @click="viewHouse()">
    <img :src="houseProp.imgUrl" />
    <h5>{{houseProp.description}}</h5>
    <h5>{{houseProp.price}}</h5>
  </div>
</template>


<script>
export default {
  name: "house",
  props: ["houseProp"],
  data() {
    return {};
  },
  computed: {},
  methods: {
    viewHouse() {
      //NOTE better way to navigate programatically
      this.$router.push({
        name: "house",
        params: { houseId: this.houseProp._id }
      });
      //NOTE The OTHER way...
      //   this.$router.push("/houses/" + this.houseProp._id);
    }
  },
  components: {}
};
</script>


<style scoped>
img {
  height: 100px;
}
</style>