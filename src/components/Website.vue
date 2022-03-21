<template>
  <div id="website">
    <headerMain></headerMain>
    <sectionVacancy></sectionVacancy>
    <footerMain></footerMain>
  </div>
</template>

<script>
import sectionVacancy from "../components/sectionVacancy.vue";
import headerMain from "../components/headerMain.vue";
import footerMain from "../components/footerMain.vue";

export default {
  name: "website",
  components: {
    headerMain,
    sectionVacancy,
    footerMain,
  },
};
</script>

<style></style>
