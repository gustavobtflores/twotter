<template>
  <header class="user-profile__header">
    <h1 class="user-profile__header-title">Twooter</h1>
    <span class="user-profile__header-username">@{{ username }}</span>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    username: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
@use "../styles/scss/variables";

.user-profile__ {
  &header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 5%;
    background-color: variables.$color-primary;

    &-title {
      font-size: 32px;
      color: variables.$color-texts;
    }

    &-username {
      color: variables.$color-texts;
      font-weight: 600;
    }
  }
}
</style>
