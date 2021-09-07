<template>
  <!-- START : Page Wrap -->
  <div class="home-page-wrap">
    <muse-header />
    <div class="body-wrap">
      <muse-nav class="muse-nav"/>
      <muse-dashboard />
    </div>
  </div>
  <!-- END : Page Wrap -->
</template>

<script>
import MuseDashboard from '../components/MuseDashboard.vue';
import MuseHeader from "../components/MuseHeader.vue";
import MuseNav from "../components/MuseNav.vue";
export default {
  name: "HomeView",

  components: { MuseHeader, MuseNav, MuseDashboard },

  directives: {},

  data() {
    return {};
  },

  computed: {
    
  },

  mounted() {},

  methods: {

  },
};
</script>

<style lang="scss" scoped>
.body-wrap {
  display: flex;
  height: calc(100vh - #{$header-height} - 2px);
  .muse-nav {
    width: 25%;
  }
}
</style>