<template>
  <div class="artist-card-wrap">
    <div class="left-wrap">
      <img
        class="artist-img"
        :src="require(`@/assets/Images/${artistDetails.img}`)"
        alt=""
      />
    </div>
    <div class="description-wrap">
      <div class="title">{{ artistDetails.name }}</div>
      <div class="play-minutes">
        <img class="icon" src="@/assets/Icons/Listening Icon.svg" alt="" />
        {{ artistDetails.playMinutes | numericCommaSeperator }} play minutes
      </div>
      <div class="liked-songs">
        <svg
          class="icon"
          width="25"
          height="22"
          viewBox="0 0 25 22"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M22.5734 1.50427C19.8977 -0.788996 15.9183 -0.376503 13.4623 2.17211L12.5004 3.16897L11.5385 2.17211C9.08734 -0.376503 5.10304 -0.788996 2.42731 1.50427C-0.639037 4.13636 -0.800167 8.86038 1.94392 11.7135L11.392 21.5249C12.0023 22.1584 12.9935 22.1584 13.6039 21.5249L23.0519 11.7135C25.8009 8.86038 25.6398 4.13636 22.5734 1.50427Z"
            fill="#E553d2"
          />
        </svg>
        {{ artistDetails.likedSongs | numericCommaSeperator }} liked songs
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MuseArtistCard",

  props: ["artistDetails"],
  filters: {
    numericCommaSeperator: function(value) {
      return Number(value).toLocaleString();
    }
  },

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
.artist-card-wrap {
  width: 100%;
  height: 150px;
  display: flex;
  border-radius: $border-radius-3;
  padding: $space-3 * 0.6;
  background: $theme-bg-shade-3;
  gap: $space-3 * 1.2;
  align-items: center;
  cursor: pointer;
  transition: transform 0.15s ease-in-out;

  &:hover {
    transform: scale(1.03);
  }

  .left-wrap {
    width: 30%;
    height: 100%;
    .artist-img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: $border-radius-3 * 0.8;
    }
  }
  
  .description-wrap {
    flex: 1;
    font-size: $font-size-sm;
    display: flex;
    flex-direction: column;
    gap: $space-1*1.3;
    .title {
      font-size: $font-size-lg;
      font-weight: 500;
      line-height: 1.7;
    }
    .play-minutes, .liked-songs {
      display: flex;
      align-items: center;
    }
    .icon {
      width: $font-size-md;
      margin-right: $space-2;
      // filter: invert(42%) sepia(93%) saturate(1352%) hue-rotate(87deg) brightness(119%) contrast(119%);
    }
  }
}
</style>