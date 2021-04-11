<template>
  <div>
    <h2>Name:{{ name }}</h2>
    <h2>ID:{{ year }}</h2>
    <ap-hom v-bind:students="students"></ap-hom>
  </div>
</template>

<script>
import Home from "./components/Home.vue";

export default {
  components: { "ap-hom": Home },
  data() {
    return {
      students: [
        {
          code: "AB123k",
          firstgrade: 60,
          twograde: 50,
          finalgrade: 90,
        },
        {
          code: "KG563c",
          firstgrade: 70,
          twograde: 98,
          finalgrade: 65,
        },
        {
          code: "KL432u",
          firstgrade: 45,
          twograde: 90,
          finalgrade: 45,
        },
        {
          code: "KL432u",
          firstgrade: 89,
          twograde: 97,
          finalgrade: 100,
        },
      ],
      year: "456923012",
      name: "Parahat Nepesov",
    };
  },
};
</script>
<style scoped>
h1 {
  color: purple;
}
</style>
