<template>
  <div class="banner-wrap">
    <img class="banner" src="@/assets/Images/Concert Background.jpeg" alt="">
    <div class="banner-content">
      <div class="left-content"><div>Best of the Decade</div> For You!</div>
      <div class="right-content">
        <div class="brand">Muse</div>
        <div class="highlight">Spotlight</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MuseBanner',

  components: {  },

  directives: {  },

  data() {
    return {
      
    };
  },

  mounted() {
    
  },

  methods: {
    
  },
};
</script>

<style lang="scss" scoped>
.banner-wrap {
  width: 100%;
  position: relative;
  height: 190px;
  border-radius: $border-radius-3;
  overflow: hidden;
  .banner {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .banner-content {
    position: absolute;
    display: flex;
    padding: $space-4 $space-4 $space-4 $space-5;
    align-items: center;
    justify-content: space-between;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(6, 6, 26, 0.28);

    .left-content {
      width: 50%;
      font-size: $font-size-3xl;
      font-weight: 700;
      line-height: 1.2;
    }
    .right-content {
      display: flex;
      height: 100%;
      flex-direction: column;
      justify-content: space-between;
      align-items: flex-end;

      .brand {
        font-family: $font-seconday;
        font-size: $font-size-xl;
        font-weight: 500;
      }
      .highlight {
        font-size: $font-size-2xl;
        font-weight: 500;
      }
    }
  }
}
</style>