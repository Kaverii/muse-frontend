<template>
  <div class="muse-player-control">
    <audio
      class="audio-input"
      controls
      src="@/assets/audio/bird-music.wav"
      ref="player"
    >
      Your browser does not support the
      <code>audio</code> element.
    </audio>
    <!-- START : Player Wrap -->
    <div class="player-wrap">
      <!-- START : Player Left Wrap -->
      <div class="left-wrap">
        <!-- START : Song Image -->
        <img
          class="songImg"
          :src="require(`@/assets/Images/${songDetails.img}`)"
          alt=""
        />
        <!-- END : Song Image -->
        <!-- START : Song Audio Controls -->
        <div class="audio-controls">
          <!-- START : Top Wrap -->
          <div class="top-wrap">
            <!-- START : Title -->
            <div class="title">
              {{ songDetails.name }} - {{ songDetails.artist }}
              <button type="button" class="fav-icon-btn">
                <i class="fa fa-heart fav-icon"></i>
              </button>
            </div>
            <!-- END : Title -->
            <!-- START : Play List Button -->
            <div class="play-list-btn">
              <!-- START : Shuffle Button -->
              <button type="button" class="shuffle btn active">
                <img
                  class="shuffle icon"
                  src="@/assets/Icons/Shuffle.svg"
                  alt=""
                />
              </button>
              <!-- END : Shuffle Button -->
              <!-- START : Repeat Button -->
              <button type="button" class="repeat btn">
                <img
                  class="repeat icon"
                  src="@/assets/Icons/Repeat.svg"
                  alt=""
                />
              </button>
              <!-- END : Repeat Button -->
            </div>
            <!-- END : Play List Button -->
          </div>
          <!-- END : Top Wrap -->
          <!-- START : Button Wrap -->
          <div class="bottom-wrap">
            <div class="elapsed-time">{{ elapsedTime }}</div>
            <ui-input-range
              class="play-range"
              :value="playerProgress"
              @rangeChange="onPlayerChange"
            />
            <div class="total-time">{{ totalTime }}</div>
          </div>
          <!-- END : Button Wrap -->
        </div>
        <!-- END : Song Audio Controls -->
      </div>
      <!-- END : Player Left Wrap -->
      <!-- START : Player Right Wrap -->
      <div class="right-wrap">
        <button type="button" class="icon-btn">
          <img src="@/assets/Icons/Angle-double-left.svg" alt="" />
        </button>
        <button type="button" class="icon-btn">
          <img
            v-if="!isPlaying"
            src="@/assets/Icons/Play icon.svg"
            alt=""
            @click="playMusic"
          />
          <i v-else class="fa fa-pause" @click="pauseMusic"></i>
        </button>
        <button type="button" class="icon-btn">
          <img src="@/assets/Icons/Angle-double-right.svg" alt="" />
        </button>
      </div>
      <!-- END : Player Right Wrap -->
    </div>
    <!-- END : Player Wrap -->
  </div>
</template>

<script>
import UiInputRange from "../lib/UiInputRange.vue";
export default {
  name: "MusePlayerControl",

  props: ["songDetails"],

  components: { UiInputRange },

  directives: {},

  data() {
    return {
      elapsedTime: "00:00",
      totalTime: "00:00",
      playerProgress: 0,
      isPlaying: false,
      intervalListener: null,
    };
  },

  mounted() {
    this.intervalListener = setInterval(() => {
      if (this.$refs.player && !this.$refs.player.paused) {
        this.isPlaying = true;
        this.totalTime = this.getTotalTime();
        this.elapsedTime = this.getElapsedTime();
        const audio = this.$refs.player;
        this.playerProgress =
          (Math.floor(audio.currentTime) / Math.floor(audio.duration)) * 100;
      } else {
        this.isPlaying = false;
      }
    }, 1000);
  },
  unmounted() {
    return clearInterval(this.intervalListener);
  },

  computed: {},

  methods: {
    //Convert audio current time from seconds to min:sec display
    convertTime(seconds) {
      const format = (val) => `0${Math.floor(val)}`.slice(-2);
      // let hours = seconds / 3600;
      const minutes = (seconds % 3600) / 60;
      return [minutes, seconds % 60].map(format).join(":");
    },

    //Show the total duration of audio file
    getTotalTime() {
      const audio = this.$refs.player;
      if (audio) {
        const seconds = audio.duration;
        return this.convertTime(seconds);
      } else {
        return "00:00";
      }
    },
    //Display the audio time elapsed so far
    getElapsedTime() {
      const audio = this.$refs.player;
      if (audio) {
        const seconds = audio.currentTime;
        return this.convertTime(seconds);
      } else {
        return "00:00";
      }
    },

    onPlayerChange(value) {
      const audio = this.$refs.player;
      if (audio) {
        audio.currentTime = Math.floor(parseFloat(value) * audio.duration);
        this.playerProgress = parseFloat(value);
        if (this.isPlaying) {
          audio.play();
        }
      }
    },

    playMusic() {
      const audio = this.$refs.player;
      if (audio) {
        audio.play();
        console.log("Royalty Free Music has been used");
      }
    },

    pauseMusic() {
      const audio = this.$refs.player;
      if (audio) {
        audio.pause();
        this.isPlaying = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.muse-player-control {
  margin-top: $space-4;
  background: $theme-bg-shade-3;
  border-radius: $border-radius-3;
  // radial-gradient(circle farthest-side at 50% 50%, $theme-bg-shade-3 70%, blue 70%, blue 80%, red 100%)
  height: 110px;
  overflow: hidden;

  .audio-input {
    position: absolute;
    height: 0;
  }
  .player-wrap {
    display: flex;
    height: 100%;

    .left-wrap {
      display: flex;
      width: 80%;
      padding: $space-2 * 1.5;

      @media only screen and (max-width: 1200px) {
        width: 75%;
      }

      .songImg {
        height: 100%;
        border-radius: $border-radius-1;
      }

      .audio-controls {
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding-left: $space-3;
        width: 100%;
        .top-wrap {
          display: flex;
          justify-content: space-between;
          align-items: center;
          .title {
            display: flex;
            font-size: $font-size-lg;
            font-weight: 500;
            line-height: 1.7;
          }
          .fav-icon-btn {
            font-size: $font-size-md;
            -webkit-text-fill-color: $theme-secondary;
            -webkit-text-stroke-width: 2px;
            -webkit-text-stroke-color: $theme-white;
            margin: 0 $space-3;
            transition: transform 200ms ease-in-out;
            &:hover {
              transform: scale(1.15);
            }
          }

          .play-list-btn {
            display: flex;
            align-items: center;
            gap: $space-2;
            .btn {
              display: block;
              padding: $space-1;
              position: relative;
              height: 34px;

              &.active::after {
                content: "";
                position: absolute;
                width: 4px;
                height: 4px;
                border-radius: 50%;
                background-color: $theme-white;
                bottom: 0;
                left: 45%;
              }

              .icon {
                transition: transform 200ms ease-in-out;
                &:hover {
                  transform: scale(1.15);
                }
              }

              .shuffle {
                height: 20px;
              }
              .repeat {
                height: 18px;
              }
            }
          }
        }

        .bottom-wrap {
          display: flex;
          align-items: center;
          padding: $space-1;
          font-size: $font-size-sm;
          font-weight: 300;
          .play-range {
            flex: 1;
            padding: $space-1 $space-2;
            display: flex;
          }
        }
      }
    }

    .right-wrap {
      width: 20%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      padding-left: $space-5;
      gap: $space-4;

      @media only screen and (max-width: 1200px) {
        width: 25%;
      }

      background: radial-gradient(
        circle at -20% 50%,
        #353965 25%,
        rgba(98, 102, 246, 0.5) 25%,
        rgba(98, 102, 246, 0.5) 30%,
        rgba(98, 102, 246, 0.75) 30%,
        rgba(98, 102, 246, 0.75) 35.5%,
        $theme-secondary 35.5%,
        $theme-primary 100%
      );

      @media only screen and (max-width: 1440px) {
        background: radial-gradient(
          circle at -25% 50%,
          #353965 30%,
          rgba(98, 102, 246, 0.5) 30%,
          rgba(98, 102, 246, 0.5) 35%,
          rgba(98, 102, 246, 0.75) 35%,
          rgba(98, 102, 246, 0.75) 40.5%,
          #6266f6 40.5%,
          #e553d2 100%
        );
      }

      @media only screen and (max-width: 1200px) {
        background: radial-gradient(
          circle at -30% 50%,
          #353965 35%,
          rgba(98, 102, 246, 0.5) 35%,
          rgba(98, 102, 246, 0.5) 40%,
          rgba(98, 102, 246, 0.75) 40%,
          rgba(98, 102, 246, 0.75) 45.5%,
          #6266f6 45.5%,
          #e553d2 100%
        );
      }

      .icon-btn {
        display: block;
        transition: transform 200ms ease-in-out;
        &:hover {
          transform: scale(1.15);
        }
        img {
          height: $font-size-xl * 1.07;
        }
        .fa {
          font-size: $font-size-xl * 1.07;
        }
      }
    }
  }
}
</style>