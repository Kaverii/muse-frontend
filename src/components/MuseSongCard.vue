<template>
  <div class="song-card">
    <img
      class="song-img"
      :src="require(`@/assets/Images/${songDetails.img}`)"
      alt=""
    />
    <div class="content-abs-wrap">
      <div class="description-wrap">
        <div class="left-wrap">
          <div class="title" :title="songDetails.name">
            {{ songDetails.name }}
          </div>
          <div class="album" :title="songDetails.album">
            {{ songDetails.album }}
          </div>
        </div>
        <button type="button" class="play-btn">
          <img src="@/assets/Icons/Play icon.svg" alt="" class="play-icon" />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MuseSongCard",

  props: ["songDetails"],

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
.song-card {
  width: 100%;
  height: 100%;
  position: relative;
  border-radius: $border-radius-3;
  overflow: hidden;
  transition: transform 0.15s ease-in-out;

  &:hover {
    transform: scale(1.03);
  }

  .song-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .content-abs-wrap {
    position: absolute;
    bottom: $space-3;
    left: 0;
    width: 100%;
    padding: $space-2 * 1.5;

    .description-wrap {
      border-radius: $border-radius-1 * 1.8;
      display: flex;
      overflow: hidden;
      -webkit-backdrop-filter: blur(5px);
      backdrop-filter: blur(5px);
      // background: radial-gradient(circle at 30% 50%, rgba(185, 90, 222, 0.2) 62%,  rgba(256, 256, 256, 0.3) 62%, rgba(256, 256, 256, 0.3) 100%);

      .left-wrap {
        width: 68%;
        padding: $space-2 * 1.2 $space-2 * 1.7;
        background-color: rgba(185, 90, 222, 0.2);

        // background: radial-gradient(circle at 40% 50%, rgba(185, 90, 222, 0.2) 82%, rgba(256, 256, 256, 0.3) 82%);

        // border-radius: $border-radius-1 22px 22px $border-radius-1;
        // box-shadow: 0 0px 0px 40vw rgba(256, 256, 256, 0.3);

        // backdrop-filter: blur(5px);

        .title,
        .album {
          white-space: nowrap;
          overflow-x: hidden;
          text-overflow: ellipsis;
        }
        .title {
          font-size: $font-size-md;
          font-weight: 500;
          margin-bottom: $space-1;
        }
        .album {
          font-size: $font-size-xs;
          font-weight: 100;
        }
      }
      .play-btn {
        flex: 1;
        display: flex;
        align-items: center;
        justify-content: center;
        background: radial-gradient(
          circle at -60% 50%,
          rgba(185, 90, 222, 0.2) 50%,
          rgba(256, 256, 256, 0.3) 50%
        );
        padding-left: 7.5%;

        .play-icon {
          width: $font-size-md;
        }
      }
    }
  }
}
</style>