<template>
  <div class="song-row-wrap">
    <div class="header">
      <div class="title">{{ title }}</div>
      <button type="button" class="see-all">SEE ALL</button>
    </div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "MuseSongRow",
  props: ["title"],

  components: {},

  directives: {},

  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped>
.song-row-wrap {
  margin: $space-4 * 1.2 0;
  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    .title {
      font-size: $font-size-2xl;
      font-weight: 500;
    }
    .see-all {
      color: $theme-primary;
      font-weight: 500;
      font-size: $font-size-xl;
      text-transform: uppercase;
    }
  }
}
</style>