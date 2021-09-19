<script>
import homes from "~/data/homes";
export default {
  name: "IndividualHome",
  head() {
    return {
      title: this.home?.title || this.$route.params.id,
    };
  },
  data() {
    return {
      home: {},
    };
  },
  created() {
    const home = homes.find((home) => home.objectID === this.$route.params.id);
    this.home = home;
  },
};
</script>

<template>
  <div v-if="home">
    <div style="display:flex">
      <img
        v-for="image in home.images"
        :key="image"
        :src="image"
        alt=""
        width="200"
        height="200"
      />
    </div>
    {{ home.title }} <br />
    {{ home.pricePerNigh }} / night <br />
    <img src="/images/marker.svg" width="20" height="20" alt="" />
    {{ home.location.address }} {{ home.location.city }}

    {{ home.location.state }} {{ home.location.country }} <br />
    <img src="/images/star.svg" width="20" height="20" alt="" />{{
      home.reviewValue
    }}
    <br />
    {{ home.guests }} guests, {{ home.bedrooms }} rooms, {{ home.beds }} beds,
    {{ home.bathrooms }} bath <br />
  </div>
  <div v-else>
    <h2>
      There is no home found for
      <strong style="color:#1dc39d;">{{ `"${$route.params.id}"` }}</strong>
    </h2>
  </div>
</template>

<style lang="scss" scoped></style>
