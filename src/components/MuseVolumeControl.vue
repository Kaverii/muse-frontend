<template>
  <!-- START : Volume Control Wrap -->
  <div class="volume-control">
    <img
      src="@/assets//Icons//Speaker volume.svg"
      alt="Speaker Volume Control Logo"
      class="speaker-icon"
    />
    <ui-input-range class="volume-range" :value="50"/>
  </div>
  <!-- END : Volume Control Wrap -->
</template>

<script>
import UiInputRange from '@/lib/UiInputRange.vue';
export default {
  name: "MuseVolumeControl",

  components: { UiInputRange },

  directives: {},

  data() {
    return {};
  },

  mounted() {},

  filters: {
    
  },

  methods: {},
};
</script>

<style lang="scss" scoped>
/* -------- START : Volume Control -------- */
.volume-control {
  display: flex;
  align-items: center;
  border-radius: $border-radius-2;
  padding: 0 $space-3 * 1.3;
  background-color: $theme-bg-shade-3;

  .speaker-icon {
    height: $font-size-lg;
    margin-right: $space-2;
  }
  .volume-range {
    width: 200px;
  }
}
/* -------- END : Volume Control -------- */
</style>