<template>
  <div class="dashboard-content-wrap">
    <muse-banner />
    <muse-song-row title="Recently played">
      <div class="songs-wrap">
        <muse-song-card
          v-for="song in songs"
          :key="song.id"
          :song-details="song"
        />
      </div>
    </muse-song-row>
    <muse-song-row title="Your favorite artists">
      <div class="artists-wrap">
        <muse-artist-card
          v-for="artist in artists"
          :key="artist.id"
          :artist-details="artist"
        />
      </div>
    </muse-song-row>
    <muse-player-control :songDetails="currentSong"/>
  </div>
</template>

<script>
import MuseBanner from "./MuseBanner.vue";
import MuseSongRow from "./MuseSongRow.vue";
import MuseSongCard from "./MuseSongCard.vue";
import MuseArtistCard from "./MuseArtistCard.vue";
import MusePlayerControl from './MusePlayerControl.vue';
export default {
  name: "MuseDashboard",

  components: { MuseBanner, MuseSongRow, MuseSongCard, MuseArtistCard, MusePlayerControl },

  directives: {},

  data() {
    return {
      songs: [
        {
          id: "1",
          name: "Sunset",
          album: "Midnight",
          img: "Sunset.jpeg",
        },
        {
          id: "2",
          name: "Stargazing",
          album: "Kygo",
          img: "Stargazing.jpeg",
        },
        {
          id: "3",
          name: "Lean on",
          album: "Major Lazer",
          img: "Lean on.jpeg",
        },
        {
          id: "4",
          name: "Here I am again",
          album: "Yerin Baek",
          img: "Here I am again.jpeg",
        },
        {
          id: "5",
          name: "Is You",
          album: "AILEE",
          img: "Is you edited.png",
        },
      ],
      artists: [
        {
          id: "1",
          name: "Taylor Swift",
          img: "Tay.jpeg",
          playMinutes: 21313,
          likedSongs: 97,
        },
        {
          id: "2",
          name: "Kygo",
          img: "KYGO.jpeg",
          playMinutes: 12688,
          likedSongs: 23,
        },
        {
          id: "3",
          name: "Phoebe Ryan",
          img: "Phoebe Ryan.jpeg",
          playMinutes: 7677,
          likedSongs: 17,
        },
      ],
      currentSong: {
          id: "5",
          name: "Enchanted",
          artist: "Taylor Swift",
          img: "Speak now tay.jpeg",
      },
    };
  },

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped>
.dashboard-content-wrap {
  width: 100%;
  height: 100%;
  overflow-y: scroll;
  padding: $space-4;
  background-color: $theme-bg-shade-2;
  border-radius: $border-radius-2;

  .songs-wrap,
  .artists-wrap {
    margin: $space-3 0;
    display: grid;
    column-gap: $space-4 * 1.2;
  }
  .songs-wrap {
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  }
  .artists-wrap {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>