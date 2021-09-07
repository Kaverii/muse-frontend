<template>
  <div class="nav-wrap">
    <nav>
      <ul>
        <li class="active">
          <div class="menu-icon">
            <img src="@/assets/Icons/Home.svg" alt="" />
          </div>
          <div class="nav-link">Home</div>
        </li>
        <li>
          <div class="menu-icon">
            <img src="@/assets/Icons/Search.svg" alt="" />
          </div>
          <div class="nav-link">Search</div>
        </li>
        <li>
          <div class="menu-icon">
            <img src="@/assets/Icons/Library.svg" alt="" />
          </div>
          <div class="nav-link">Library</div>
        </li>
        <li>
          <div class="menu-icon">
            <img src="@/assets/Icons/Heart.svg" alt="" />
          </div>
          <div class="nav-link">Favorites</div>
        </li>
      </ul>
    </nav>
    <div class="bottom-button">
      <button class="outline-btn" type="button">
        <span class="text">Subscribe</span>
        <i class="fa fa-check-square icon"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "MuseNav",

  components: {},

  directives: {},

  data() {
    return {};
  },

  computed: {
    subIcon() {
      return require("@/assets/Icons/Subscription check mark.svg");
    },
  },

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped>
.nav-wrap {
  width: 100%;
  height: 100%;
  padding: 0 $space-4 $space-3 $space-4;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-size: $font-size-xl;

  nav ul {
    li {
      padding: $space-3 * 1.3;
      display: flex;
      align-items: center;
      cursor: pointer;
      
      &.active, &:hover {
        background: linear-gradient(to right, $theme-secondary, $theme-primary);
        border-radius: $border-radius-3;
      }

      .menu-icon {
        margin-right: $space-3 * 1.2;
        width: $font-size-xl;
        img {
          width: 100%;
        }
      }
      .nav-link {
        font-weight: 500;
      }
    }
  }

  .outline-btn {
    width: 100%;
    display: flex;

    padding: $space-3;
    font-size: $font-size-xl;
    font-weight: 700;
    justify-content: center;
    align-items: center;

    border-radius: $border-radius-3;
    box-shadow: 0 0 6px 0 rgba(157, 96, 212, 0.5);
    border: solid 5px transparent;
    background-image: linear-gradient(
        rgba(255, 255, 255, 0),
        rgba(255, 255, 255, 0)
      ),
      linear-gradient(to bottom, $theme-secondary -50%, $theme-primary);
    background-origin: border-box;
    background-clip: content-box, border-box;
    box-shadow: 2px 1000px 1px $theme-bg-shade-1 inset;

    .text {
      background: linear-gradient($theme-secondary -50%, $theme-primary);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-transform: uppercase;
    }

    .icon {
      color: $theme-primary;
      display: block;
      background: -webkit-linear-gradient($theme-secondary -50%, $theme-primary);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-left: $space-3;
    }
  }
}
</style>