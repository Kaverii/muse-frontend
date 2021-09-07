<template>
  <!-- START : Header -->
  <header class="header">
    <!-- START : Header Left Wrap -->
    <div class="header-left-wrap">
      <!-- START : Logo -->
      <a href="#" class="logo">
        <img
          src="@/assets/Icons/MUSE LOGO.svg"
          alt="Muse Logo"
          class="logo-img"
        /> </a
      ><!-- END : Logo -->
    </div>
    <!-- END : Header Left Wrap -->

    <!-- START : Header Right Wrap -->
    <div class="header-right-wrap">
      <muse-volume-control />
      <muse-profile-menu />
    </div>
    <!-- END : Header Right Wrap -->
  </header>
  <!-- END : Header -->
</template>

<script>
import MuseProfileMenu from './MuseProfileMenu.vue';
import MuseVolumeControl from "./MuseVolumeControl.vue";
export default {
  name: "Museheader",

  components: { MuseVolumeControl, MuseProfileMenu },

  directives: {},

  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: $space-3 * 1.3 $space-4;
  background-color: $theme-bg-shade-1;

  /* -------- START : Logo -------- */
  .logo {
    display: block;
    padding: $space-1;
    img {
      height: 100%;
    }
  }
  /* -------- END : Logo -------- */

  /* -------- START : Header Right -------- */
  .header-right-wrap {
    display: flex;
    gap: $space-4;
  }
  /* -------- END : Header Right -------- */
}
</style>