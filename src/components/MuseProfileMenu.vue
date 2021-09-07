<template>
  <div class="profile-header-menu">
    <img src="@/assets/Images/Profile Picture.png" alt="" class="profile-dp" />
    <div class="username">Aziz Stark</div>
    <img src="@/assets/Icons/Drop down.svg" alt="" srcset="" class="dropdown-icon"/>
  </div>
</template>

<script>
export default {
  name: "MuseProfileMenu",

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
/* -------- START : Header Profile Menu  -------- */
.profile-header-menu {
  display: flex;
  border-radius: $border-radius-2;
  padding: $space-1;
  background-color: $theme-bg-shade-3;
  width: 220px;
  justify-content: space-between;
  align-items: center;

  .profile-dp {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  .username {
    font-size: $font-size-lg;
    color: $theme-white;
    line-height: 1.6;
    font-weight: 500;
  }
  .dropdown-icon {
    margin-right: $space-3;
  }
}
/* -------- END : Header Profile Menu -------- */
</style>