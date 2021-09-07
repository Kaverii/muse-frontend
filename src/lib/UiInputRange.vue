<template>
  <div class="input-range-wrap">
    <input
      type="range"
      min="0"
      max="100"
      :value="value"
      step="0.5"
      @change="onRangeChange"
    />
  </div>
</template>

<script>
export default {
  name: "AppInputRange",

  props: {
    value: {
      type: String
    }
  },

  components: {},

  directives: {},

  data() {
    return {};
  },

  mounted() {},

  methods: {
    onRangeChange(event) {
      this.$emit("rangeChange", event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.input-range-wrap {
  padding: $space-2 0;
  height: 20px;
  &:hover input[type="range"]::-webkit-slider-thumb {
    background: white;
  }
}

input[type="range"] {
  margin: auto;
  display: block;
  -webkit-appearance: none;
  overflow: hidden;
  height: 4px;
  width: 100%;
  cursor: pointer;
  border-radius: 2px; /* iOS */

  &::-moz-range-progress {
    height: 4px;
    background: linear-gradient(to right, #6266f6 0%, #e553d2 100%);
    outline: none;
  }
  &::-moz-range-thumb {
    width: 8px;
    background-color: $theme-white;
    display: none;
  }
  &::-moz-range-thumb {
    width: 8px;
    background-color: $theme-white;
  }
  &::-moz-range-track {
    height: 4px;
    background-color: #202344;
    outline: none;
  }
}

::-webkit-slider-runnable-track {
  background: linear-gradient(to right, #6266f6 0%, #e553d2 100%);
}

::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 8px; /* 1 */
  height: 4px;
  background: transparent;
  border-radius: 1px;
  transition: background-color 100ms linear;
  box-shadow: 100vw 0 0 100vw #202344;
}
</style>