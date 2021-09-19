<script>
import homes from "../data/homes.json";
export default {
  head() {
    return {
      title: "HomePage",
      meta: [
        {
          name: "description",
          content: "This is a Homepage..!",
        },
      ],
    };
  },
  data() {
    return {
      homes: homes.slice(0, 3),
    };
  },
};
</script>

<template>
  <div>
    <div
      v-for="home in homes"
      :key="home.objectID"
      style="float: left; margin: 1rem"
    >
      <nuxt-link :to="`/home/${home.objectID}`" prefetch>
        <HomeCard :home="home" />
      </nuxt-link>
    </div>
  </div>
</template>

<style scoped></style>
